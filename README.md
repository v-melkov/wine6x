`sudo -y yum group install "Development tools"`

Для поддержки 32-битных систем установливаем:  
`yum install glibc-devel.i686`

Обязательные пакеты (кроме Xinerama (мультимониторы)):  

    sudo yum install mingw32-gcc mingw64-gcc pulseaudio-libs-devel.i686 pulseaudio-libs-devel dbus-devel.i686 dbus-devel fontconfig-devel.i686 fontconfig-devel freetype-devel.i686 freetype-devel gnutls-devel.i686 gnutls-devel libjpeg-turbo-devel.i686 libjpeg-turbo-devel libpng-devel.i686 libpng-devel libtiff-devel mesa-libGL-devel.i686 mesa-libGL-devel libunwind-devel.i686 libunwind-devel libxml2-devel.i686 libxml2-devel libxslt-devel.i686 libxslt-devel libX11-devel.i686 libX11-devel libXcomposite-devel.i686 libXcomposite-devel libXcursor-devel.i686 libXcursor-devel libXfixes-devel.i686 libXfixes-devel libXinerama-devel.i686 libXinerama-devel libXrandr-devel.i686 libXrandr-devel libXrender-devel.i686 libXrender-devel

Необязательные, но желательные пакеты:  

    sudo yum install libFAudio-devel.i686 libFAudio-devel gstreamer1-devel.i686 gstreamer1-devel gstreamer1-plugins-base-devel.i686 gstreamer1-plugins-base-devel mpg123-devel.i686 mpg123-devel mesa-libOSMesa-devel.i686 mesa-libOSMesa-devel libvkd3d-devel.i686 libvkd3d-devel vulkan-headers vulkan-loader.i686 vulkan-loader

Дальше загружаем исходники:  
`wget https://dl.winehq.org/wine/source/6.0/wine-6.0.tar.xz`

Распаковываем:  
`tar -xvf wine-6.0.tar.xz -C wine-source`

Создаём пару директорий для работы:  
`mkdir wine{32,64}-build`  

переходим в 64-битную версию:  
`cd wine64-build`  
`../wine-source/configure --enable-win64`  
`make -j17`

32 бита:  
`cd ../wine32-build`
`PKG_CONFIG_PATH=/usr/lib ../wine-source/configure --with-wine64=../wine64-build`  
`make`   
