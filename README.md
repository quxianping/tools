工具
=========
各种工具的安装和使用

# linux
=======================================
### ffmpeg
音频、视频格式转换，默认带有N多解码器，主流格式都可以解码，但是转换还需要编码库，这个需要自己下载
实际开发中，主要是ios的音频格式caf(acc)到mp3的转换，以及android的3gp(amr_nb)到mp3的转换

(1)需要下载mp3编码库
lame-3.99.5.tar.gz
http://sourceforge.net/projects/lame/
只需要配置prefix

(2)安装ogg和vorbis库
libogg-1.3.1.tar.gz和libvorbis-1.3.3.tar.gz
http://xiph.org/downloads/
只需要配置prefix

(2)安装ffmpeg
FFmpeg-master.zip
https://github.com/FFmpeg/FFmpeg
非root用户，需要配置--extra-cflags和--extra-ldflags
./configure --prefix=/home/work/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --disable-yasm --disable-ffserver --disable-ffplay --extra-cflags="-I /home/work/ffmpeg/include" --extra-ldflags="-L /home/work/ffmpeg/lib" --enable-libvorbis

使用时
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/work/ffmpeg/lib
/home/work/ffmpeg/bin/ffmpeg -i tmp4.caf -acodec libmp3lame tmp4.mp3