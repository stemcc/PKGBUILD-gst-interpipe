# Maintainer: Steph McCormick (stemcc) <stephan@idiolx.com>

pkgname=gst-interpipe
pkgver=1.1.8
pkgrel=1
pkgdesc="GStreamer plug-in for interpipeline communication"
arch=(x86_64)
license=("LGPL2.1")

url="https://github.com/RidgeRun/gst-interpipe"

depends=(
    gstreamer
    gst-plugins-base
    gtk-doc
)

makedepends=(
    git
    meson
    valgrind
)
provides=("libgstinterpipe.so")

source=(
    $pkgname-$pkgver.tar.gz::https://github.com/RidgeRun/$pkgname/archive/refs/tags/v$pkgver.tar.gz
)
sha256sums=(SKIP)

build() {
    cd $pkgname-$pkgver
    arch-meson ../build --prefix=/usr \
        -D enable-gtk-doc=false
    ninja -C ../build
}

check() {
    cd $pkgname-$pkgver
    meson test -C ../build --print-errorlogs
}

package() {
    cd $pkgname-$pkgver

    meson install -C ../build --destdir "$pkgdir"
}
