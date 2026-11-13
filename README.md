# Varman device agent

Installers for the Varman device agent. The agent checks disk encryption,
antivirus, password policy and screen lock, and reports them to your
organization in [Varman](https://varman.io). After installing, open the agent
and sign in with your work account to link the device.

Your employee portal also has a download button for your platform.

## macOS (Homebrew)

```sh
brew tap varman-io/tap
brew trust varman-io/tap
brew install --cask varman-device-agent
```

Recent Homebrew versions only load casks from third-party taps you trust,
hence `brew trust`.

Or download the `.dmg` for your Mac (Apple Silicon `arm64`, Intel `x64`) from
[Releases](https://github.com/varman-io/device-agent/releases/latest).

The app is not notarized yet. On first launch, if macOS says it cannot verify
the app, open **System Settings > Privacy & Security** and click **Open Anyway**.

## Debian / Ubuntu (apt)

```sh
curl -fsSL https://varman-io.github.io/device-agent/varman-packages.gpg \
  | sudo tee /usr/share/keyrings/varman.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/varman.gpg] https://github.com/varman-io/device-agent/releases/download/apt ./" \
  | sudo tee /etc/apt/sources.list.d/varman.list
sudo apt update && sudo apt install varman-device-agent
```

## Fedora / RHEL / Rocky (dnf, yum)

```sh
sudo curl -fsSL -o /etc/yum.repos.d/varman.repo https://varman-io.github.io/device-agent/varman.repo
sudo dnf install varman-device-agent
```

## Windows

Download `Varman-Device-Agent-<version>-setup.exe` from
[Releases](https://github.com/varman-io/device-agent/releases/latest) and run it.
The installer is not code-signed yet: if Windows shows "Windows protected your
PC", click **More info**, then **Run anyway**.

## Verify a download

Each release has a `SHA256SUMS` file. The apt and yum metadata is signed with
the Varman Packages key, fingerprint
`3BFB 0A41 609F 7435 32D7  8441 C32F 28F0 1EEC CE15`.
