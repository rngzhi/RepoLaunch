# escape=`
FROM mcr.microsoft.com/windows/servercore:ltsc2025

SHELL ["powershell","-NoLogo","-NoProfile","-Command"]

# 1) Chocolatey
RUN Set-ExecutionPolicy Bypass -Scope Process -Force; `
    [System.Net.ServicePointManager]::SecurityProtocol = `
        [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
    iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1')); `
    choco feature enable -n=usePackageExitCodes; `
    choco feature enable -n=allowGlobalConfirmation;

# 2) Toolchain & utils
RUN choco install -y git; choco install -y nvm; & "$env:ChocolateyInstall\helpers\chocolateyProfile.psm1"; refreshenv;

RUN nvm install lts; nvm use lts; node --version; npm --version; npx --version;


