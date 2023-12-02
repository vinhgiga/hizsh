# Hizsh

History/auto-complete menu, powerlevel10k prompt for zsh and pacman animation on Windows Terminal (Click on the image below to watch a step-by-step tutorial video).

[![Introduction](/intro.png)](https://youtu.be/4j8xEdOmgps)

## Installation

### Zsh installation

1. Download and run [Msys2 installer](https://www.msys2.org/#installation). It’s as simple as Next, Next, Next and Finish.
2. A terminal for the UCRT64 environment will launch. To install Zsh, run the following commands:

   ```bash
   # pacman configuration
   $ sed -i '/^Color$/a ILoveCandy' /etc/pacman.conf
   # Installing zsh
   $ pacman -S zsh
   ```

### Zsh configuration

#### Install Nerd Font

1. Download these four ttf files:
   - [MesloLGS NF Regular.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
   - [MesloLGS NF Bold.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
   - [MesloLGS NF Italic.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
   - [MesloLGS NF Bold Italic.ttf](
       https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)
2. Double-click on each file and click "Install". This will make `MesloLGS NF` font available to all
   applications on your system.

#### Using my configuration

Folder structure:

```
C:/
├── giga
│   ├── data
│   │   ├── assets
│   │   │   └── pacman.gif
│   │   └── zsh-windows
│   │   │   ├── .p10k.zsh
│   │   │   ├── .zshrc
│   │   │   ├── docker-zsh-completion
│   │   │   ├── fast-syntax-highlighting
│   │   │   ├── powerlevel10k
│   │   │   └── zsh-autocomplete
```

Configuration:

1. On UCRT64 terminal, run the following commands to install zsh plugins:

    ```bash
    $ mkdir -p /c/giga/data/zsh-windows /c/giga/data/assets
    $ cd /c/giga/data/zsh-windows
    $ echo 'export ZDOTDIR=/c/giga/data/zsh-windows' >> /etc/zsh/zshenv
    $ git clone https://github.com/marlonrichert/zsh-autocomplete
    $ git clone https://github.com/zdharma-continuum/fast-syntax-highlighting
    $ git clone https://github.com/romkatv/powerlevel10k
    $ git clone https://github.com/greymd/docker-zsh-completion
    ```

2. Copy the [.p10k.zsh](/.p10k.zsh), [.zshrc](/.zshrc) files from this repository to the `C:\giga\data\zsh-windows` folder.

### Windows Terminal and Visual Studio Code setup

#### Windows Terminal

1. On Windows Terminal, click the menu (down-arrow) button > select the Settings option > click on Open JSON file.
2. Update the Windows Terminal `settings.json` file as follows:

    ```
    // This makes UCRT64 the default shell
    "defaultProfile": "{17da3cac-b318-431e-8a3e-7fcdefe6d114}",
    "profiles": {
    "list":
        [
            {
                "backgroundImage": "C:\\giga\\data\\assets\\pacman.gif",
                "backgroundImageAlignment": "bottomRight",
                "backgroundImageStretchMode": "uniform",
                "commandline": "C:/msys64/msys2_shell.cmd -use-full-path -defterm -here -no-start -ucrt64 -shell zsh",
                "guid": "{17da3cac-b318-431e-8a3e-7fcdefe6d114}",
                "icon": "C:/msys64/ucrt64.ico",
                "name": "UCRT64 / MSYS2",
                "startingDirectory": "%USERPROFILE%",
                "font": {
                    "face": "MesloLGS NF",
                    "size": 12
                }
            }
        ]
    }
    ```

3. Place the [pacman.gif](/pacman.gif) file to the `C:\giga\data\assets` folder.

#### Visual Studio Code

1. On Visual Studio Code, press the <kbd>F1</kbd> key to access the Command Palette. Type `settings json` in the search bar and select the `Preferences: Open User Settings (JSON) command`.
2. Update the Visual Studio Code `settings.json` file as follows:

    ```
    "terminal.integrated.fontFamily": "MesloLGS NF",
    "terminal.integrated.minimumContrastRatio": 1,
    "terminal.integrated.defaultProfile.windows": "MSYS2 UCRT",
    "terminal.integrated.profiles.windows": {
        "MSYS2 UCRT": {
        "path": "cmd.exe",
        "args": [
            "/c",
            "C:\\msys64\\msys2_shell.cmd -use-full-path -defterm -here -no-start -ucrt64 -shell zsh"
        ]
        }
    }
    ```

### Key bindings

| Key(s)                       | Action                            |
| ---------------------------- | --------------------------------- |
| <kbd>Tab</kbd>               | Auto-complete menu                |
| <kbd>↑</kbd> <kbd>↓</kbd>    | History fuzzy search menu         |
| <kbd>Ctrl</kbd>+<kbd>D</kbd> | Exit                              |
| <kbd>Ctrl</kbd>+<kbd>L</kbd> | Clear screen                      |
| <kbd>Ctrl</kbd>+<kbd>R</kbd> | Toggle history/auto-complete menu |
| <kbd>Ctrl</kbd>+<kbd>U</kbd> | Clear the entire line of input    |
| <kbd>Ctrl</kbd>+<kbd>Z</kbd> | Undo                              |

## License

This project is licensed under the MIT License.  See the [LICENSE](/LICENSE) file
for details.
