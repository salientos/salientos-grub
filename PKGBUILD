# Maintainer: Philip Müller <philm[at]manjaro[dot]org>
# Maintainer: Stefano Capitani <stefano[at]manjaro[dot]org>
# Contributor: Helmut Stult

# Arch credits:
# Based on the file created for Arch Linux by:
# Contributor : Christian Hesse <mail@eworm.de>
# Contributor : Ronald van Haren <ronald.archlinux.org>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Keshav Amburay <(the ddoott ridikulus ddoott rat) (aatt) (gemmaeiil) (ddoott) (ccoomm)>

# Modified for Salient OS By : Silent Robot <d3signr[at]gmail[dot]com>

## "1" to enable IA32-EFI build in Arch x86_64, "0" to disable
_IA32_EFI_IN_ARCH_X64="1"

## "1" to enable EMU build, "0" to disable
_GRUB_EMU_BUILD="1"

[[ "${CARCH}" == 'x86_64' ]] && _EFI_ARCH='x86_64'
[[ "${CARCH}" == 'i686' ]] && _EFI_ARCH='i386'
[[ "${CARCH}" == 'aarch64' ]] && _EFI_ARCH='aarch64'

[[ "${CARCH}" == 'x86_64' ]] && _EMU_ARCH='x86_64'
[[ "${CARCH}" == 'i686' ]] && _EMU_ARCH='i386'
[[ "${CARCH}" == 'aarch64' ]] && _EMU_ARCH='aarch64'

pkgname=grub
pkgdesc="GNU GRand Unified Bootloader (2)"
_commit='2f4430cc0a44fd8c8aa7aee5c51887667ad3d6c3'
_unifont_ver='15.0.01'
_pkgver=2.06.r261.g2f4430cc0
pkgver=${_pkgver/-/}
pkgrel=2
arch=('x86_64' 'i686' 'aarch64')
url='https://www.gnu.org/software/grub/'
license=('GPL3')
backup=('etc/default/grub'
        'etc/grub.d/40_custom'
        'boot/grub/grub.cfg')
install="${pkgname}.install"
options=('!makeflags')
provides=('grub-common' 'grub-bios' 'grub-emu' "grub-efi-${_EFI_ARCH}")
conflicts=('grub-common' 'grub-bios' 'grub-emu' "grub-efi-${_EFI_ARCH}" 'grub-legacy')
replaces=('grub-common' 'grub-bios' 'grub-emu' "grub-efi-${_EFI_ARCH}")
makedepends=('git' 'rsync' 'xz' 'freetype2' 'ttf-dejavu' 'python' 'autogen'
             'texinfo' 'help2man' 'gettext' 'device-mapper' 'fuse2')
depends=('sh' 'xz' 'gettext' 'device-mapper')
optdepends=('freetype2: For grub-mkfont usage'
            'fuse2: For grub-mount usage'
            'dosfstools: For grub-mkrescue FAT FS and EFI support'
            'lzop: For grub-mkrescue LZO support'
            'efibootmgr: For grub-install EFI support'
            'libisoburn: Provides xorriso for generating grub rescue iso using grub-mkrescue'
            'os-prober: To detect other OSes when generating grub.cfg in BIOS systems'
            'mtools: For grub-mkrescue FAT FS support')

if [[ "${_GRUB_EMU_BUILD}" == "1" ]]; then
    makedepends+=('libusb' 'sdl')
    optdepends+=('libusb: For grub-emu USB support'
                 'sdl: For grub-emu SDL support')
fi

validpgpkeys=('E53D497F3FA42AD8C9B4D1E835A93B74E82E4209'  # Vladimir 'phcoder' Serbinenko <phcoder@gmail.com>
              'BE5C23209ACDDACEB20DB0A28C8189F1988C2166'  # Daniel Kiper <dkiper@net-space.pl>
              '95D2E9AB8740D8046387FD151A09227B1F435A33') # Paul Hardy <unifoundry@unifoundry.com>

source=("git+https://git.savannah.gnu.org/git/grub.git#commit=${_commit}"
        'git+https://git.savannah.gnu.org/git/gnulib.git'
        "https://ftp.gnu.org/gnu/unifont/unifont-${_unifont_ver}/unifont-${_unifont_ver}.bdf.gz"
        '0001-00_header-add-GRUB_COLOR_-variables.patch'
        'grub-export-path.patch'
        'grub-salientos-modifications.patch'
        'grub-salientos-theme.patch'
        'grub-use-efivarfs.patch'
        '0001-grub-maybe_quiet.patch'
        '0002-grub-gettext_quiet.patch'
        '0003-grub-quick-boot.patch'
        'background.png'
        'grub.default'
        'sbat.csv'
        'grub.cfg'
        'update-grub'
        'grub-set-bootflag'
        "${pkgname}.hook")

sha256sums=('SKIP'
            'SKIP'
            '1fddba900a36b8a067bf2177b05c4a2482a0f7ca1545cf531c03509f47ce1590'
            '5dee6628c48eef79812bb9e86ee772068d85e7fcebbd2b2b8d1e19d24eda9dab'
            '63c611189a60d68c6ae094f2ced91ac576b3921b7fd2e75a551c2dc6baefc35e'
            '2e67843994fa309de2246391daa105cce350ac7edb51aed5f76ffbc37cb38bc4'
            'adaa13a25fdc0179c0d446cb426bf71b63606225e8620a6a3e30243f6dc0c30b'
            '20b2b6e7f501596b5cce6ffa05906980427f760c03d308d0e045cf2ecf47bb0e'
            'b6041a0b27f9febeaf1d065d45ec786a61ea4a94c2dbdbddb27cbb2348873702'
            '39d7843dfe1e10ead912a81be370813b8621794a7967b3cc5e4d4188b5bf7264'
            '4cae03685c238a60169f1134165ff010faebddb5b3218d92d32e0b6729b27656'
            'bdfa1a3bd422351765b76136734a7f9ff2442d6bad8fb4f3f8cc527dfbe4a73a'
            'c548894a6f5ea1a3fdc6858bfb6c8c2612749e3dd5c507c162914b77397e57b5'
            '89bbfe11cec0a07f5b0f170cde35abcc4cbf16d8db7b4920435525f71527fc10'
            '7fc95d49c0febe98a76e56b606a280565cb736580adecf163bc6b5aca8e7cbd8'
            'a6a3e6a7c2380aff66b6096d478aed790c927ceed551ce52c0c454191eb4e3aa'
            '2eb199f510340cf8d190ba2fa80d5bdcf1e2e7ca53e8011af2ee62ea3b8dd03b'
            'b9fbe1395d1e4961f3d39feb3804049c5f7a6007ca389695a71f6f22279bf921')
            
_backports=(
)

_configure_options=(
	PACKAGE_VERSION="${pkgver}-${pkgrel}"
	FREETYPE="pkg-config freetype2"
	BUILD_FREETYPE="pkg-config freetype2"
	--enable-mm-debug
	--enable-nls
	--enable-device-mapper
	--enable-cache-stats
	--enable-boot-time
	--enable-grub-mkfont
	--enable-grub-mount
	--enable-quiet-boot
	--enable-quick-boot	
	--prefix="/usr"
	--bindir="/usr/bin"
	--sbindir="/usr/bin"
	--mandir="/usr/share/man"
	--infodir="/usr/share/info"
	--datarootdir="/usr/share"
	--sysconfdir="/etc"
	--program-prefix=""
	--with-bootdir="/boot"
	--with-grubdir="grub"
	--disable-silent-rules
	--disable-werror
)

prepare() {
	cd "${srcdir}/grub/"

	echo "Apply backports..."
	local _c
	for _c in "${_backports[@]}"; do
		git log --oneline -1 "${_c}"
		git cherry-pick -n "${_c}"
	done

	echo "==> Patch to enable GRUB_COLOR_* variables in grub-mkconfig..."
	## Based on http://lists.gnu.org/archive/html/grub-devel/2012-02/msg00021.html
	patch -Np1 -i "${srcdir}/0001-00_header-add-GRUB_COLOR_-variables.patch"

	# https://github.com/calamares/calamares/issues/918
	echo "Use efivarfs modules"
	patch -Np1 -i "${srcdir}/grub-use-efivarfs.patch"

	echo "==> Patch to export $PATH"
	patch -Np1 -i "${srcdir}/grub-export-path.patch"
	
	echo "==> Patch to include SalientOS Modifications"
	patch -Np1 -i "${srcdir}/grub-salientos-modifications.patch"
	patch -Np1 -i "${srcdir}/grub-salientos-theme.patch"

	echo "==> Add Ubuntu patches"
	echo "0001"
	patch -Np1 -i "${srcdir}/0001-grub-maybe_quiet.patch"
	echo "002"
	patch -Np1 -i "${srcdir}/0002-grub-gettext_quiet.patch"
	echo "0003"
	patch -Np1 -i "${srcdir}/0003-grub-quick-boot.patch"

	echo "Fix DejaVuSans.ttf location so that grub-mkfont can create *.pf2 files for starfield theme..."
	sed 's|/usr/share/fonts/dejavu|/usr/share/fonts/dejavu /usr/share/fonts/TTF|g' -i "configure.ac"

	echo "Fix mkinitcpio 'rw' FS#36275..."
	sed 's| ro | rw |g' -i "util/grub.d/10_linux.in"

	echo "Fix OS naming FS#33393..."
	sed 's|GNU/Linux|Linux|' -i "util/grub.d/10_linux.in"

	echo "Bump Version to ${pkgver}~${pkgrel}~manjaro"
	sed -i -e "s|${pkgver}|${pkgver}~${pkgrel}~manjaro|g" "configure.ac"

	echo "Pull in latest language files..."
	./linguas.sh

	echo "Avoid problem with unifont during compile of grub..."
	# http://savannah.gnu.org/bugs/?40330 and https://bugs.archlinux.org/task/37847
	gzip -cd "${srcdir}/unifont-${_unifont_ver}.bdf.gz" > "unifont.bdf"

	echo "Run bootstrap..."
	./bootstrap \
		--gnulib-srcdir="${srcdir}/gnulib/" \
		--no-git

	echo "Make translations reproducible..."
	sed -i '1i /^PO-Revision-Date:/ d' po/*.sed
}

_build_grub-common_and_bios() {
	echo "Set ARCH dependent variables for bios build..."
	if [[ "${CARCH}" == 'x86_64' ]]; then
		_EFIEMU="--enable-efiemu"
	else
		_EFIEMU="--disable-efiemu"
	fi

	echo "Copy the source for building the bios part..."
	cp -r "${srcdir}/grub/" "${srcdir}/grub-bios/"
	cd "${srcdir}/grub-bios/"

	echo "Unset all compiler FLAGS for bios build..."
	unset CFLAGS
	unset CPPFLAGS
	unset CXXFLAGS
	unset LDFLAGS
	unset MAKEFLAGS

	echo "Run ./configure for bios build..."
	./configure \
		--with-platform="pc" \
		--target="i386" \
		"${_EFIEMU}" \
		--enable-boot-time \
		"${_configure_options[@]}"

	if [ ! -z "${SOURCE_DATE_EPOCH}" ]; then
		echo "Make info pages reproducible..."
		touch -d "@${SOURCE_DATE_EPOCH}" $(find -name '*.texi')
	fi

	echo "Run make for bios build..."
	make
}

_build_grub-efi() {
	echo "Copy the source for building the ${_EFI_ARCH} efi part..."
	cp -r "${srcdir}/grub/" "${srcdir}/grub-efi-${_EFI_ARCH}/"
	cd "${srcdir}/grub-efi-${_EFI_ARCH}/"

	echo "Unset all compiler FLAGS for ${_EFI_ARCH} efi build..."
	unset CFLAGS
	unset CPPFLAGS
	unset CXXFLAGS
	unset LDFLAGS
	unset MAKEFLAGS

	echo "Run ./configure for ${_EFI_ARCH} efi build..."
	./configure \
		--with-platform="efi" \
		--target="${_EFI_ARCH}" \
		--disable-efiemu \
		--enable-boot-time \
		"${_configure_options[@]}"

	echo "Run make for ${_EFI_ARCH} efi build..."
	make
}

_build_grub-emu() {
	echo "Copy the source for building the emu part..."
	cp -r "${srcdir}/grub/" "${srcdir}/grub-emu/"
	cd "${srcdir}/grub-emu/"

	echo "Unset all compiler FLAGS for emu build..."
	unset CFLAGS
	unset CPPFLAGS
	unset CXXFLAGS
	unset LDFLAGS
	unset MAKEFLAGS

	echo "Run ./configure for emu build..."
	./configure \
		--with-platform="emu" \
		--target="${_EMU_ARCH}" \
		--enable-grub-emu-usb=no \
		--enable-grub-emu-sdl=no \
		--disable-grub-emu-pci \
		"${_configure_options[@]}"

	echo "Run make for emu build..."
	make
}

build() {
	cd "${srcdir}/grub/"

	echo "Build grub bios stuff..."
	_build_grub-common_and_bios

	echo "Build grub ${_EFI_ARCH} efi stuff..."
	_build_grub-efi

	if [[ "${CARCH}" == "x86_64" ]] && [[ "${_IA32_EFI_IN_ARCH_X64}" == "1" ]]; then
		echo "Build grub i386 efi stuff..."
		_EFI_ARCH="i386" _build_grub-efi
	fi

	if [[ "${_GRUB_EMU_BUILD}" == "1" ]]; then
		echo "Build grub emu stuff..."
		_build_grub-emu
	fi
}

_package_grub-common_and_bios() {
	cd "${srcdir}/grub-bios/"

	echo "Run make install for bios build..."
	make DESTDIR="${pkgdir}/" bashcompletiondir="/usr/share/bash-completion/completions" install

	echo "Remove gdb debugging related files for bios build..."
	rm -f "${pkgdir}/usr/lib/grub/i386-pc"/*.module || true
	rm -f "${pkgdir}/usr/lib/grub/i386-pc"/*.image || true
	rm -f "${pkgdir}/usr/lib/grub/i386-pc"/{kernel.exec,gdb_grub,gmodule.pl} || true

	echo "Install grub.cfg for backup array"
	install -D -m0644 "${srcdir}/grub.cfg" "${pkgdir}/boot/grub/grub.cfg"

	echo "Install update-grub"
	install -Dm755 "${srcdir}/update-grub" "${pkgdir}/usr/bin/update-grub"

	echo "Install grub background"
	install -Dm644 "${srcdir}/background.png" "${pkgdir}/usr/share/grub/background.png"	

	echo "Install /etc/default/grub (used by grub-mkconfig)"
	install -D -m0644 "$srcdir"/grub.default "$pkgdir"/etc/default/grub

	echo "Install 99-${pkgname}.hook"
	install -D -m644 "${srcdir}/${pkgname}.hook" "${pkgdir}/usr/share/libalpm/hooks/99-${pkgname}.hook"

	# workaround for quiet fsck
	install -D -m755 "${srcdir}/grub-set-bootflag" "${pkgdir}/usr/bin/grub-set-bootflag"
}

_package_grub-efi() {
	cd "${srcdir}/grub-efi-${_EFI_ARCH}/"

	echo "Run make install for ${_EFI_ARCH} efi build..."
	make DESTDIR="${pkgdir}/" bashcompletiondir="/usr/share/bash-completion/completions" install

	echo "Remove gdb debugging related files for ${_EFI_ARCH} efi build..."
	rm -f "${pkgdir}/usr/lib/grub/${_EFI_ARCH}-efi"/*.module || true
	rm -f "${pkgdir}/usr/lib/grub/${_EFI_ARCH}-efi"/*.image || true
	rm -f "${pkgdir}/usr/lib/grub/${_EFI_ARCH}-efi"/{kernel.exec,gdb_grub,gmodule.pl} || true

	sed -e "s/%PKGVER%/${pkgver}-${pkgrel}/" < "${srcdir}/sbat.csv" > "${pkgdir}/usr/share/grub/sbat.csv"
}

_package_grub-emu() {
	cd "${srcdir}/grub-emu/"

	echo "Run make install for emu build..."
	make DESTDIR="${pkgdir}/" bashcompletiondir="/usr/share/bash-completion/completions" install

	echo "Remove gdb debugging related files for emu build..."
	rm -f "${pkgdir}/usr/lib/grub/${_EMU_ARCH}-emu"/*.module || true
	rm -f "${pkgdir}/usr/lib/grub/${_EMU_ARCH}-emu"/*.image || true
	rm -f "${pkgdir}/usr/lib/grub/${_EMU_ARCH}-emu"/{kernel.exec,gdb_grub,gmodule.pl} || true
}

package() {
	cd "${srcdir}/grub/"

	echo "Package grub ${_EFI_ARCH} efi stuff..."
	_package_grub-efi

	if [[ "${CARCH}" == "x86_64" ]] && [[ "${_IA32_EFI_IN_ARCH_X64}" == "1" ]]; then
		echo "Package grub i386 efi stuff..."
		_EFI_ARCH="i386" _package_grub-efi
	fi

	if [[ "${_GRUB_EMU_BUILD}" == "1" ]]; then
		echo "Package grub emu stuff..."
		_package_grub-emu
	fi

	echo "Package grub bios stuff..."
	_package_grub-common_and_bios

	# Don't overwrite /usr/share/info/dir
	rm "$pkgdir/usr/share/info/dir"
}

