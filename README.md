# R-conda-problems
some common problems when install R packages in conda environment

1. install package 'ragg' in conda-based R
Error log:
  * installing *source* package 'ragg' ...
  ** package 'ragg' successfully unpacked and MD5 sums checked
  staged installation is only possible with locking
  ** using non-staged installation
  Found pkg-config cflags and libs!
  Using PKG_CFLAGS=-I/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/x86_64-linux-gnu
  Using PKG_LIBS=-L/build/libjpeg-turbo-6HlDLQ/libjpeg-turbo-2.0.3/obj-x86_64-linux-gnu/lib/x86_64-linux-gnu -lfreetype -lpng16 -lz -ltiff -ljpeg -ljpeg
  -----------------------------[ ANTICONF ]-------------------------------
  Configuration failed to find one of freetype2 libpng libtiff-4 libjpeg. Try installing:
   * deb: libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev (Debian, Ubuntu, etc)
   * rpm: freetype-devel libpng-devel libtiff-devel libjpeg-turbo-devel (Fedora, CentOS, RHEL)
   * csw: libfreetype_dev libpng16_dev libtiff_dev libjpeg_dev (Solaris)
  If freetype2 libpng libtiff-4 libjpeg is already installed, check that 'pkg-config' is in your
  PATH and PKG_CONFIG_PATH contains a freetype2 libpng libtiff-4 libjpeg.pc file. If pkg-config
  is unavailable you can set INCLUDE_DIR and LIB_DIR manually via:
  R CMD INSTALL --configure-vars='INCLUDE_DIR=... LIB_DIR=...'
  -------------------------- [ERROR MESSAGE] ---------------------------
  In file included from /root/miniconda3/envs/jupyterlab/x86_64-conda-linux-gnu/sysroot/usr/include/features.h:361,
                   from /root/miniconda3/envs/jupyterlab/x86_64-conda-linux-gnu/sysroot/usr/include/limits.h:27,
                   from /root/miniconda3/envs/jupyterlab/lib/gcc/x86_64-conda-linux-gnu/9.3.0/include-fixed/limits.h:194,
                   from /root/miniconda3/envs/jupyterlab/lib/gcc/x86_64-conda-linux-gnu/9.3.0/include-fixed/syslimits.h:7,
                   from /root/miniconda3/envs/jupyterlab/lib/gcc/x86_64-conda-linux-gnu/9.3.0/include-fixed/limits.h:34,
                   from /usr/include/libpng16/pngconf.h:31,
                   from /usr/include/libpng16/png.h:339,
                   from <stdin>:2:
  /usr/include/x86_64-linux-gnu/sys/cdefs.h:492:49: error: missing binary operator before token "("
    492 | #if __GNUC_PREREQ (4,8) || __glibc_clang_prereq (3,5)
        |                                                 ^
  In file included from /root/miniconda3/envs/jupyterlab/x86_64-conda-linux-gnu/sysroot/usr/include/stdio.h:932,
                   from /usr/include/libpng16/pngconf.h:46,
                   from /usr/include/libpng16/png.h:339,
                   from <stdin>:2:
  /usr/include/x86_64-linux-gnu/bits/stdio2.h:228:17: error: missing binary operator before token "("
    228 | #if __GLIBC_USE (DEPRECATED_GETS)

Solutions:
  install.packages("ragg", configure.vars=c("INCLUDE_DIR=/usr/include/freetype2 LIB_DIR=/usr/lib/x86_64-linux-gnu/pkgconfig/"))
  install.packages("ragg", configure.vars = c("INCLUDE_DIR=/usr/include/freetype2 -I/usr/include/libpng16 -I/usr/include/x86_64-linux-gnu LIB_DIR=/usr/lib/x86_64-linux-gnu/pkgconfig/")) # add more include dir, add '-I' for the second or later dir 
  
  refer to: https://stackoverflow.com/questions/53324885/how-to-include-more-paths-under-include-dir-in-configure-vars-argument-in-instal
 
 2. waiting for more
