pkgname=visual-studio-code-insiders
_pkgbuildnumber=1677586939
_pkgversion=1.76.0_insider
pkgver="${_pkgversion}+${_pkgbuildnumber}"
pkgrel=1
pkgdesc="Editor for building and debugging modern web and cloud applications (insiders version)"
arch=('x86_64')
url="https://code.visualstudio.com/"
license=('custom: commercial')
depends=(
  'libxkbfile'
  'gnupg'
  'gtk3'
  'libsecret'
  'nss'
  'gcc-libs'
  'libnotify'
  'libxss'
  'glibc'
  'lsof' # terminal splitting, see https://github.com/Microsoft/vscode/issues/62991
)
optdepends=(
  "glib2: Needed for move to trash functionality"
  "libdbusmenu-glib: Needed for KDE global menu"
)

_src_x86_64="https://update.code.visualstudio.com/latest/linux-x64/insider"
source_x86_64=(
  "code_insider_x64_${_pkgbuildnumber}.tar.gz::${_src_x86_64}"
  "${pkgname}.desktop"
  "${pkgname}-url-handler.desktop"
  "${pkgname}-bin.sh"
)

_main_desktop_sha256='9ebe80f2fe463a82747bf39013ff3406054707f01a503e9545a6f6556a36b0de'
_url_handler_desktop_sha256='dc854ca319cad429ddc13b6d0646d295d249d82fab4f565ae63eec13d572c049'
_main_bin_sha256='67d83f676135ca14806aab7292361a4a737f3076527860258176c886cdb3f0c1'
sha256sums_x86_64=(
  'dc92be6acb711df3697040c37033fafeb183809cb91e19f824391f8421557e7a'
  "${_main_desktop_sha256}"
  "${_url_handler_desktop_sha256}"
  "${_main_bin_sha256}"
)

package() {
  _pkg=VSCode-linux-x64

  install -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -d "${pkgdir}/opt/${pkgname}"
  install -d "${pkgdir}/usr/bin"
  install -d "${pkgdir}/usr/share/applications"
  install -d "${pkgdir}/usr/share/icons" 

  install -m644 "${srcdir}/${_pkg}/resources/app/LICENSE.rtf" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE.rtf"
  install -m644 "${srcdir}/${_pkg}/resources/app/resources/linux/code.png" "${pkgdir}/usr/share/icons/${pkgname}.png"
  install -m644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
  install -m644 "${srcdir}/${pkgname}-url-handler.desktop" "${pkgdir}/usr/share/applications/${pkgname}-url-handler.desktop"

  cp -r "${srcdir}/${_pkg}/"* "${pkgdir}/opt/${pkgname}" -R

  # Launcher
  install -m755 "${srcdir}/${pkgname}-bin.sh" "${pkgdir}/usr/bin/code-insiders"
}
