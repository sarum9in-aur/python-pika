# Maintainer: Aleksey Filippov <sarum9in@gmail.com>
# Maintainer: Massimiliano Torromeo <massimiliano.torromeo@gmail.com>
# Contributor: Christopher Arndt <aur -at- chrisarndt -dot- de>

_pkgbase=pika
pkgname=(python-${_pkgbase} python2-${_pkgbase})
pkgver=0.13.0
pkgrel=1
pkgdesc="A pure-Python implementation of the AMQP 0-9-1 protocol"
arch=(any)
url="http://pika.readthedocs.org/"
license=('GPL')
depends=()
makedepends=('python-setuptools' 'python2-setuptools')
source=("https://github.com/$_pkgbase/$_pkgbase/archive/$pkgver.tar.gz")
sha256sums=('8038953b651bd6905f3d611cd354de17b3e53dcaf62977a732be0ddc7cd83b60')

build() {
  cd "$srcdir/$_pkgbase-$pkgver"

  rm -rf ../buildpy3; mkdir ../buildpy3
  python setup.py build -b ../buildpy3

  rm -rf ../buildpy2; mkdir ../buildpy2
  python2 setup.py build -b ../buildpy2
}

package_python-pika() {
  depends=(python)

  cd "$srcdir/$_pkgbase-$pkgver"
  rm -rf build; ln -s ../buildpy3 build
  python setup.py install --skip-build -O1 --root="$pkgdir"
  install -m0644 -D "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

  chmod -R a+r "$pkgdir/usr/lib"
}

package_python2-pika() {
  depends=(python2)

  cd "$srcdir/$_pkgbase-$pkgver"
  rm -rf build; ln -s ../buildpy2 build
  python2 setup.py install --skip-build -O1 --root="$pkgdir"
  install -m0644 -D "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

  chmod -R a+r "$pkgdir/usr/lib"
}
