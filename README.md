
# Installations



![](https://weeblytutorials.com/wp-content/uploads/2018/10/install-Weebly-Apps.jpeg)

## Overview

We'll be installing all of the tools necessary for Unit 1 in this lesson.

***It is so important that you follow all of these instructions to a T, without skipping ahead.  It is also very important, when working in the terminal, to ensure that you type everything exactly correctly before running the command. You are interacting with your computer's inner configurations, and each command should be treated with care and intention.***

## Slack

We'll be using Slack to register attendance and communicate during class. Follow the instructions below to sign up for Slack.

- Visit the following [site](https://slack.com/downloads) to download the desktop application.
- You should definitely ***not*** be using the browser version of Slack.
- Upload a ***clear*** and ***professional*** profile picture to Slack.
- Your Slack name should be your ***full name*** and not a username or nickname. This helps your instructors and classmates get to know you and interact with you.

---

## Browsers

In order to become efficient JavaScript developers, we'll utilize any one of these recommended browsers:

- [Chrome](https://www.google.com/chrome/)
- [Brave](https://brave.com/)

**Safari is not included on this list due to specific features that are not cross compatible with other browsers.**

## MacOS Users...

### Installing Homebrew

Homebrew is a package manager for MacOS. It makes installing other programs fast and easy.

To install Homebrew, paste the following command into your terminal and hit the <kbd>return</kbd> key:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

This command will perform the installation for you.

---

### Installing Zsh and Oh-My-Zsh

#### Zsh Installation

What is Zsh? Zsh is a shell designed for interactive use. It provides us with useful shortcuts to execute terminal commands faster and also enables auto completion for those commands.

To install Zsh, execute the following command in your terminal:

```sh
brew install zsh
```

#### Oh-My-Zsh Installation

What is Oh-My-Zsh?

> Oh My Zsh is an open source, community-driven framework for managing your Zsh configuration. It comes with a bunch of features out of the box and improves your terminal experience.

It also provides us with preset themes to make reading our terminal _much_ easier.

To install Oh-My-Zsh, execute the following commands in your terminal:

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

```sh
chsh -s $(which zsh)
```

### Installing NodeJS

What is NodeJS? NodeJS is a JavaScript runtime that allows us to execute JavaScript outside of a browser.

To intall NodeJS, execute the following command in your terminal:

```sh
brew install node
```

To confirm your installation, execute the following in your terminal:

```sh
node -v
```

You should see a node version listed.

### Installing Git

Git is a version control manager that we'll be using in conjunction with GitHub to manage code updates during this course.

To install Git, execute the following command in your terminal:

```sh
brew install git
```

Once the installation completes, execute the following commands in your terminal, **_one by one_**, with your ***own*** information inserted:

```sh
git config --global user.name "Your Actual Name Here"
```

```sh
git config --global user.email "your_email@example.com"
```

The name and email should be ***your*** name and email that you use on GitHub.

#### Setting Up GitHub Authentication

Github has gone through a major security change in the past few seasons. If these steps do not work for you, there is an additional way for us to do this posted below


In order for GitHub to deem our machines as "safe" to push code, we need to setup an identification key known as an SSH Key
Enter the following commands in your terminal, with your ***own*** information inserted:

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

The above email ***must*** be your GitHub email!

You should see the following prompt:

```sh
> Enter a file in which to save the key (/Users/you/.ssh/id_ed25519):
```

Leave it blank and hit <kbd>return</kbd> to save it in a default file.

You'll now be prompted to password protect the ssh key, but we can skip this portion. When prompted with the following, **hit** <kbd>return</kbd> **to leave the password as blank, both times**:

```sh
> Enter passphrase (empty for no passphrase):
> Enter same passphrase again:
```

Now, let's start the MacOS ssh-agent. Enter the following command into your terminal:

```sh
eval "$(ssh-agent -s)"
```

Now copy the ssh key to your clipboard with this command:

```sh
pbcopy < ~/.ssh/id_rsa.pub
```

To complete this setup, follow the instructions starting from Step 2 at this link **[HERE](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)**.

To check your installation, run:

```bash
ssh git@github.com
```

You should see output similar to:

```
Hi <you>! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

If you are seeing an error that looks something like "Github has changed its security features... please enter a Personal Access Token..." please let your instructional team know, we will be following this resource https://github.com/seir-123/Github-PAT-setup to set that up if needed



### Installing VSCode

VSCode is going to be our text editor of choice throughout the course. It provides us with a wonderful environment to run and test our code.

To install VSCode, execute the following command in your terminal:

```sh
brew install --cask visual-studio-code
```

Verify your installation by running:

```sh
code .
```

This command should open a new VSCode window.

#### If the `code .` command does not work for you...

Open VSCode manually from your Applications folder.

Once a VSCode window opens, press and hold <kbd>cmd</kbd> + <kbd>shift</kbd> + <kbd>P</kbd> to open the _command palette_. In the command palette, type in `path` and choose the option:

> Shell Command: Install `code` command in PATH.

This should enable the ability to open VSCode from terminal with the `code .` command. Try it out.


## Windows Subsystem Linux (WSL)

#### Installing WSL

Open `powershell` as an **admin**. Once powershell opens, run the following command within that shell:

```ps
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

**NOTE**: In order to install WSL2, your machine must meet the following requirements:

> - For x64 systems: Version 1903 or higher, with Build 18362 or higher.
> - For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
> - Builds lower than 18362 do not support WSL2. Use the Windows Update Assistant to update your version of Windows.

Now we'll enable the virtual machine feature in your machine. WSL runs in a _virtual environment_. It's like running a computer inside of another computer!

Enter the following in `powershell` with **admin** privileges:

```ps
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

**At this point, you must restart your machine!**

### Installing The Linux Kernal Update Package

Install the following package from this **[LINK](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)**

It's safe I promise!

Open `powershell` again with **admin** privileges and enter the following command:

```ps
wsl --set-default-version 2
```

Let's install our Linux distribution. We recommend Ubuntu 18.04 which you can download **[HERE](https://www.microsoft.com/store/apps/9N9TNGVNDL3Q)**. It will take you directly to the Microsoft store.

Once you reach the Microsoft store, click the `Get` button to download and install Ubuntu 18.04.

Once the download completes, you should be prompted with a terminal window:

![Bash](https://docs.microsoft.com/en-us/windows/wsl/media/ubuntuinstall.png)

Enter a username and password. We recommend setting these the same as your Windows OS login!

Now let's ensure that the Ubuntu environment is on WSL2. Enter the following into `powershell` as an **admin**:

```ps
wsl --list --verbose
```

From the list given, find the Ubuntu instance and add the information to the next command:

```ps
wsl --set-version <distribution name> <versionNumber>
```

Once these steps are completed, you should be able to open your Ubuntu environment by selecting it from your start menu. We recommend pinning it to your taskbar. Keep the Ubuntu terminal open for the remainder of this walkthrough.

#### Updating Packages

Before proceeding, run the following command in your terminal or Ubuntu:

```sh
sudo apt update
```

#### Installing Git

Git is a version control manager that we'll be utilizing throughout this program. Install it by entering the following command into your terminal:

```sh
sudo apt-get install git
```

Let's configure Git.

Enter the following commands into your terminal:

```sh
git config --global user.name "Your Name"
```

Replace `Your Name` with your name from GitHub.

```sh
git config --global user.email "youremail@domain.com"
```

Replace `youremail@domain.com` with the email you have registered with GitHub.

### Setting Up Our GitHub SSH Keys

SSH keys are used to identify machines/users via an encoded key.

To create a SSH key, enter the following command in your terminal:

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

**NOTE**: Be sure to replace `your_email@example.com` with the email that you have registered with GitHub.

When you're prompted to `Enter a file in which to save the key,` press <kbd>Enter</kbd>. This accepts the default file location.

When prompted for a password, hit <kbd>Enter</kbd> twice to skip this step:

```sh
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

We'll now start the SSH agent, enter the following command into your terminal:

```sh
eval "$(ssh-agent -s)"
```

Now enter the following command into your terminal:

```sh
ssh-add ~/.ssh/id_rsa.pub
```

Now let's install `xclip`. `xclip` is used so that we can copy items into our clipboard. Enter the following command into your terminal:

```sh
sudo apt-get install xclip
```

Now we can copy our SSH key:

```sh
xclip -selection clipboard < ~/.ssh/id_rsa.pub
```

Follow the steps outlined **[HERE](https://docs.github.com/en/github/authenticating-to-github/adding-a-new-ssh-key-to-your-github-account)** starting from Step 2. We've already completed Step 1.

### Installing Zsh and Oh-My-Zsh

#### Installing Zsh

Zsh is an extension of the regular bash shell that many computers use as default. It provides us with features that the regular bash shell does not have.

Install Zsh by running the following command in your terminal:

```sh
sudo apt install zsh -y
```

#### Installing Oh-My-Zsh

Oh-My-Zsh is an extension of the Zsh prompt. It provides us with useful information in a clear and legible format.

Install Oh-My-Zsh by running the following command in your terminal:

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

A prompt will appear to ask if you want to switch your shell to Zsh, select `yes`.

Close your terminal and re-open it. Oh-My-Zsh should now load by default.

### Installing VSCode

VSCode is going to be our text editor of choice for this course.

You can download it **[HERE](https://code.visualstudio.com/download)**.

Once downloaded, go ahead and run the installer. Once the installer completes, open VSCode.

#### Installing the WSL Remote Extension

Once you open VSCode, you may be prompted to install the Remote WSL Extension. Go ahead and do so. If you are not prompted, you can download it **[HERE](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)**.

Type in `code .` in your terminal.
This should open a VSCode window.

If the above does not work, open VSCode. It will be located in your Applications folder. Once a VSCode window opens, press and hold <kbd>cmd</kbd> + <kbd>shift</kbd> + <kbd>P</kbd> to open the command palette. In the command palette, type in `path` and choose the option:

Shell Command: Install code command in PATH.

Select this option and reconfirm the `code .` command in your terminal.

### Installing NodeJS

NodeJS is a runtime environment that allows us to run JavaScript outside of a browser.

First we'll update the apt sources for the latest node version:

```sh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash
```

Next open your `.zshrc` file with: `code ~/.zshrc` and add the following line in the first available space:

```sh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

To install NodeJS, run the following command in your terminal:

```sh
nvm install --lts
```

**Restart your terminal.**

Confirm the installation with the following command:

```sh
node --version
```

#### NPM Installation

`npm` comes with nodejs, however we need to confirm that it was installed correctly.

Confirm the installation with the following command:

```sh
npm --version
```

Change the persmissions for the npm folder:

```sh
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
export PATH=~/.npm-global/bin:$PATH
```

## Windows Native (This is an optional path for those with advanced windows skills as you will have to rely on your own intuition for installs)

### Installing VS Code

VSCode is going to be our text editor of choice for this course.

You can download it **[HERE](https://code.visualstudio.com/download)**.

Once downloaded, go ahead and run the installer. Once the installer completes, open VSCode.


### Installing GitBash

Gitbash allows your PC to run code as if it is in a UNIX enviorment, allowing you to interface with your code from your terminal.


Install the x64 bit version from the link below.

When offered to select your default code editor, make sure to select VS Code.

```sh
https://git-scm.com/download/win
```

Follow the instructions below after opening the file.

## Select Components

Select All Check boxes except Additional Icons/On The Desktop.

![image](https://user-images.githubusercontent.com/100214696/214721011-2e0db980-c92c-4e16-9012-e63d799cab04.png)

## Choosing The Default Editor Used By Git

Select use Studio Code as Git's default editor.

![image](https://user-images.githubusercontent.com/100214696/214721453-c1f34ad3-36e8-49d9-a149-4cedc4705c07.png)

## Adjusting The Name Of The Inital Branch In New Repositories

Select override and confirm the name in the textfield is main.

![image](https://user-images.githubusercontent.com/100214696/214721687-f9530c6d-ba47-4b64-aa58-ced3a9886954.png)

## Adjusting Path Enviornment

Select Git from the command line and also third party software.

![image](https://user-images.githubusercontent.com/100214696/214721798-58b3ff96-e70c-44ac-8d1b-9bf79b883763.png)

## Choosing the SSH executable

Select use bundled OpenSSH.

![image](https://user-images.githubusercontent.com/100214696/214722019-2047ed2a-adc3-4f71-8b7a-a70237ab6808.png)

## Choosing HTTPS transport backend

Select use the OpenSSL library.

![image](https://user-images.githubusercontent.com/100214696/214722127-dea1c928-dd2d-47f3-a694-a8898a38683b.png)

## Configuring the line ending conversations.

Select checkout windows-style, commit Unit-style line endings

![image](https://user-images.githubusercontent.com/100214696/214722445-bffe5110-7a9b-4842-9fc2-938664528a9a.png)

## Configuring the terminal emulator to use with Git Bash.

Select Use Windows default console window.

![image](https://user-images.githubusercontent.com/100214696/214950182-49927e0a-e607-42ea-9839-8ded82ede436.png)

## Choose the default behavior of git pull

Select Default.

![image](https://user-images.githubusercontent.com/100214696/214723099-9d22a4a9-2505-44ca-ba39-8ba8b544e585.png)

## Choose Credential Helper

Select Git Credential Manager.

![image](https://user-images.githubusercontent.com/100214696/214725095-cff2e9be-70e7-402a-bce0-13b725e9249a.png)

## Configuring Extra Options

Select Enable file system caching.

## Configuring Experimental Support 

Select none.

Click Install.

### Installing Node.JS

Install the 64x .msi version from the link below.

```sh
https://nodejs.org/en/download/
```

## Custom Setup 

After opening and getting passed the inital setup screen you'll be met with this section.

![image](https://user-images.githubusercontent.com/100214696/214727722-f9a4ec8f-bad4-446d-9f78-60bb03a52e3e.png)

Click next.

## Tools For Native Modules

![image](https://user-images.githubusercontent.com/100214696/214730833-ed9f94d9-c864-46f5-9a5d-b0039991f133.png)

Select check the box.

Press next click install.

## Terminal Prompts

You will be met with your native terminal as seen below.

![image](https://user-images.githubusercontent.com/100214696/214728607-cf710f3f-1595-4476-ae73-7f4c4b7bc646.png)

Press any key as prompted.

After a brief wait it will ask for powershell to make changes, allow.

It will spend some time loading and downloading dependancies, you'll be met with something that looks like the photo below. This denotes that the process is complete and you can close the window.

![image](https://user-images.githubusercontent.com/100214696/214728848-87953129-8216-4822-baa3-66cc829a7eb2.png)

### Confirming Node Installation

Open Git Bash from your windows search tool

![image](https://user-images.githubusercontent.com/100214696/214949524-101be97d-2873-401a-96b0-fe2fbe9d461e.png)

Inside of the terminal simply type in node and you should get the current version

![image](https://user-images.githubusercontent.com/100214696/214953280-03cc149c-f084-414a-855d-2051e19bc1f8.png)

Press CTRL + C to exit the node shell

Lastly, to ensure all packages were correctly installed type 
```sh
npm --v
```

