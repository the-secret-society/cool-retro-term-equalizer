# cool-retro-term-equalizer
   
   
equalizer using cool-retro-term, cava &amp; ncmpcpp
   
- cool-retro-term  https://github.com/Swordfish90/cool-retro-term
- cava https://github.com/karlstav/cava
- ncmpcpp  https://github.com/arybczak/ncmpcpp
  
      
   
Fix for 'module "QMLTermWidget" is not installed':
 
 
```sh
if [ "$1" ]; then addvline=$1$'\n'; fi
sudo cat <<EOT > /bin/cool-retro-term
#!/bin/bash
${addvline}
exec /home/$USER/cool-retro-term/cool-retro-term
EOT
```
 
 
```sh
pacman -S --needed --noconfirm \
base-devel fftw ncurses alsa-lib iniparser pulseaudio \
libmpdclient curl taglib ncurses fftw boost boost-libs qt5-base qt5-declarative \
qt5-quickcontrols2 qt5-graphicaleffects qmltermwidget
```
  
```sh
git clone --recursive https://github.com/Swordfish90/cool-retro-term.git
cd cool-retro-term
qmake && make
sudo make install
```
  
```sh
git clone --recursive https://github.com/arybczak/ncmpcpp.git
cd ncmpcpp
./autogen.sh
./configure
make
sudo make install
```
  
```sh
git clone --recursive https://github.com/karlstav/cava.git
cd cava 
./autogen.sh
./configure
make
sudo make install
```
  
  
```sh
git clone https://github.com/dpayne/cli-visualizer#cli-visualizer
cdcli-visualizer#cli-visualizer
mkdir build/
cd build/
cmake ../ && make clean && make -j$(nproc) && sudo make install
cd ..

if [ -z "$XDG_CONFIG_HOME" ]
then
    CONFIG_DIR=$HOME/.config/vis
else
    CONFIG_DIR=$XDG_CONFIG_HOME/vis
fi

#create config directory
mkdir -p "$CONFIG_DIR/colors"

#copy over example files
cp examples/config $CONFIG_DIR/
cp examples/rainbow $CONFIG_DIR/colors/rainbow
cp examples/basic_colors $CONFIG_DIR/colors/basic_colors
```
