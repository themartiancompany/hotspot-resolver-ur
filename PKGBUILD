# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
pkgname=hotspot-resolver
pkgver=0.0.0.0.0.0.0.0.0.0.0.0.1.1.1
_commit="aa5532cdd43e475b4ce4cf31629c9ba9944a3a2f"
pkgrel=1
_pkgdesc=(
  "Returns addresses for hostnames"
  "connected to an hotspot."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  AGPL3
)
depends=(
  "iproute2"
  "libcrash-bash"
  "net-tools"
)
_os="$( \
  uname \
    -o)"
optdepends=(
)
[[ "${_os}" == "GNU/Linux" ]] && \
[[ "${_os}" != "Android" ]] && \
  depends+=(
    'wireless_tools'
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  depends+=(
    'wireless-tools'
  )
makedepends=(
  make
)
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
[[ "${_offline}" == "true" ]] && \
  url="file://${HOME}/${pkgname}"
[[ "${_git}" == true ]] && \
  makedepends+=(
    "git"
  ) && \
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}"
  ) && \
  sha256sums+=(
    SKIP
  )
[[ "${_git}" == false ]] && \
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _tar="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum='b245547bdcdbfeb09f400305a4b515b6d49635be90f560a39302761fc2688571'
  elif [[ "${_tag_name}" == "commit" ]]; then
    _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="0fbc5af30325af46c1ca15cbdbbc6639c8b4f430a3fbc91af5269b6b53ad1451"
  fi && \
    source+=(
      "${_tar}"
    ) && \
    sha256sums+=(
      "${_sum}"
    )

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et
