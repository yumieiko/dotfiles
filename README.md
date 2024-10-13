# Arch Linux Dotfiles

<p style="text-align:center;">trademarkowo`s (yumi) Dotfiles for Arch Linux</p>

<p style="text-align:center;">
    <h1 style="text-align:center;">Global Installation</h1>
</p>

<p style="text-align:center;">
    <div style="text-align:center;">Install Yay</div>
</p>

```bash
 sudo pacman -S --needed git base-devel
 git clone https://aur.archlinux.org/yay.git
 cd yay
 makepkg -si
                                    -- or --
 chmod +x installyay.sh
 ./installyay.sh
  
```

<p style="text-align:center;">
    <h1 style="text-align:center;">Installation</h1>
</p>

<p style="text-align:center;">
    <div style="text-align:center;">Install dependencies</div>
</p>

```bash
 sudo pacman -S --needed git base-devel
 git clone https://aur.archlinux.org/yay.git
 cd yay
 makepkg -si
 yay -Syu
 yay -S waybar hyprpaper ttf-jetbrains-mono-nerd \
        alacritty kitty zsh mangohud
```

<p style="text-align:center;">
    <div style="text-align:center;">Install zsh plugins</div>
</p>

```bash
  git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
  git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

<p style="text-align:center;">
    <div style="text-align:center;">Copy Dotfiles</div>
</p>

```bash
  cp .zshrc ~/
  cp -r hypr ~/.config
  cp -r MangoHud ~/.config
  cp -r wallpapers ~/.config
  cp -r waybar ~/.config
```
### P.S: Edit ur home floder name in ~/.config/hypr/hyprpaper.conf

<p style="text-align:center;">
    <h1 style="text-align:center;">Driver Installation</h1>
</p>

### P.S: Original Link for tutorial https://github.com/korvahannu/arch-nvidia-drivers-installation-guide
### P.S: Warning! following command only for my pc, see documentation on official repo!!!


<p style="text-align:center;">
    <div style="text-align:center;">Edit pacman.conf and enable multilib</div>
</p>

```bash
  sudo nano /etc/pacman.conf
```
Find [multilib] tag and uncomment, then update system repos with following command
```bash
  yay -Syu
```

<p style="text-align:center;">
    <div style="text-align:center;">Install driver packages</div>
</p>


```bash
 yay -S nvidia nvidia-utils lib32-nvidia-utils
 yay -S nvidia-settings
                                    -- or --
 chmod +x install-nvidia-driver.sh
 ./install-nvidia-driver.sh
```

<p style="text-align:center;">
    <div style="text-align:center;">Enable nvidia DRM</div>
</p>


```bash
 cd /boot/loader/entries/
 sudo nano <filename>.conf
 -------------------------
 Append nvidia-drm.modeset=1 to the options line
```

<p style="text-align:center;">
    <div style="text-align:center;">Add Early Loading of NVIDIA Modules</div>
</p>


```bash
 sudo nano /etc/mkinitcpio.conf
 ------------------------------
 Update the line to: MODULES=(nvidia nvidia_modeset nvidia_uvm nvidia_drm)
 On the HOOKS=() line, find the word kms inside the parenthesis and remove it
 ------------------------------
 sudo mkinitcpio -P
```


<p style="text-align:center;">
    <h1 style="text-align:center;">Meow >.<</h1>
</p>