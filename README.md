# rzg2l_vlp3.05_qt5.10.1

Renesas rzg2l manifest VLP 3.05 for Qt 5.10.1


Tested on Ubuntu 20.04 LTS

$ repo init -u https://git.qt.io/renesas_qt5.10.1/repo_manifest -b qt5.10.1 -m manifest-vlp_305_qt5.10.1.xml
$ repo sync --no-clone-bundle





Download codec & graphics-lib


Download the proprietary packages and decompress them into meta-rz-features directory at $WORK directory.

https://www.renesas.com/us/en/document/sws/rz-mpu-video-codec-library-evaluation-version-rzv2l-rtk0ef0045z15001zj-v110enzip?r=1496691
https://www.renesas.com/us/en/document/swo/rz-mpu-graphics-library-evaluation-version-v112-rzg2l-and-rzg2lc-rtk0ef0045z13001zj-v112xxzip?r=1467981




Build



Generate OE default environment

$ TEMPLATECONF=$PWD/meta-renesas/meta-rzg2l/docs/template/conf/ source poky/oe-init-build-env build




Enable Qt5

$ bitbake-layers add-layer ../meta-qt5




Enable Codec

$ bitbake-layers add-layer ../meta-rz-features/meta-rz-codecs




Enable Graphics

$ bitbake-layers add-layer ../meta-rz-features/meta-rz-graphics




Build the target file system image using bitbake:

$ export MACHINE=smarc-rzg2l
$ bitbake core-image-<target>

$ ### To generate SDK, use populate_sdk task
$ bitbake -c populate_sdk core-image-<target>



target: qt, bsp (not tested), weston (not tested)
