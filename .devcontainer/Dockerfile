FROM mcr.microsoft.com/devcontainers/base:ubuntu

# Install common utilities, tmux, neovim, and gpg
USER root

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
  && apt-get -y install --no-install-recommends \
  tmux \
  neovim \
  gpg \
  gnupg2 \
  pass \
  curl \
  git \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

# Install uv (Astral's ultra-fast Python package manager)
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /usr/local/bin/

# Ensure the vscode/devcontainer user has ownership 
USER vscode
ENV PATH="/home/vscode/.local/bin:${PATH}"
