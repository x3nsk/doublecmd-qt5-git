# Maintainer: none

pkgname=doublecmd-qt5-git
pkgver=1.1.0a.r10301.aca79a3b3
pkgrel=1
pkgdesc="twin-panel (commander-style) file manager (QT5)"
arch=(x86_64)
url=https://doublecmd.sourceforge.io/
license=(GPL2)
conflicts=(doublecmd doublecmd-qt doublecmd-qt5)
depends=(qt5-base qt5-x11extras qt5-webkit qt5pas)
makedepends=(fpc lazarus)
source=("git+https://github.com/doublecmd/doublecmd.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/doublecmd"
  printf "1.1.0a.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "$srcdir/doublecmd"
        sed -i -- 's/=$(which lazbuild)/="$(which lazbuild) --lazarusdir=\/usr\/lib\/lazarus"/' build.sh
        sed -i -- 's/LIB_SUFFIX=64/LIB_SUFFIX=/' install/linux/install.sh
	lcl=qt5 ./build.sh beta
}

package() {
	cd "$srcdir/doublecmd"
        install/linux/install.sh --install-prefix="${pkgdir}"
}

