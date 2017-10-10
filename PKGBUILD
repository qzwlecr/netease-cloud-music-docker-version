# Maintainer: qzwlecr <qzwlecr@gmail.com>

pkgname=netease-cloud-music-docker-version
pkgver=1.0.0_2
pkgrel=1
pkgdesc="Use docker to avoid netease-music bugs"
arch=('i686' 'x86_64')
url="https://github.com/qzwlecr/netease-cloud-music-docker-version"
groups=('base-devel')
depends=('docker' 'bash')
conflicts=('netease-cloud-music')
source=(
    "http://s1.music.126.net/download/pc/netease-cloud-music_1.0.0-2_amd64_ubuntu16.04.deb"
    "http://music.163.com/html/web2/service.html"
    "netease-cloud-music"
)
md5sums=('d9a6fa79ffcb654254a1d8b7ba5901a3'
         'SKIP'
         'SKIP')

package() {
  chmod +x ${pkgdir}/usr/lib/netease-cloud-music/libcef.so
}
prepare(){
    docker info &>/dev/null
}

package() {
    docker pull qzwlecr/netease-cloud-music-docker-version
    cd ${srcdir}
    tar -xvf data.tar.xz -C ${pkgdir}
    install -D -m644 service.html ${pkgdir}/usr/share/licenses/$pkgname/license.html
    install -m755 netease-cloud-music ${pkgdir}/usr/bin/netease-cloud-music
    rm -rf ${pkgdir}/usr/lib/netease-cloud-music
}
