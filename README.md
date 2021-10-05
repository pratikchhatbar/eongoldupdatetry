# eongoldupdatetry
Trying to update EON gold with NOT-most-up-to-date software

Currently, the URL https://raw.githubusercontent.com/commaai/openpilot/release2/installer/updater/update.json shows this content:
{
  "ota_url": "https://commadist.azureedge.net/neosupdate/ota-signed-5dc2575d713977666a8e14ae1b43a04d7f63123934c80fa10751d949a107653e.zip",
  "ota_hash": "5dc2575d713977666a8e14ae1b43a04d7f63123934c80fa10751d949a107653e",
  "recovery_url": "https://commadist.azureedge.net/neosupdate/recovery-f01a55c9ba52ca57668d1684c6bf4118efd31916b04f8c1fcd8495013d3677eb.img",
  "recovery_len": 15222060,
  "recovery_hash": "f01a55c9ba52ca57668d1684c6bf4118efd31916b04f8c1fcd8495013d3677eb"
}

However, the URL https://github-wiki-see.page/m/commaai/openpilot/wiki/Unofficial-Hardware says:

openpilot 0.8.3 dropped the support for EON (OnePlus 3T), therefore openpilot 0.8.2 is the last supported version for OnePlus 3T. Installing the latest version of NEOS as-is will result in bootlooping into bootloader. If you're planning to use EON (OnePlus 3T), modifying the update.json file to fetch the older OTA file is required.

Open eon-neos-master folder and find update.json file. Replace the contents with following:

{
  "ota_url": "https://commadist.azureedge.net/neosupdate/ota-signed-827a2324b19e5ff45ec3553b8f73afa3ac8b9fafa3415df6e93926733deaa07c.zip",
  "ota_hash": "827a2324b19e5ff45ec3553b8f73afa3ac8b9fafa3415df6e93926733deaa07c",
  "recovery_url": "https://commadist.azureedge.net/neosupdate/recovery-db31ffe79dfd60be966fba6d1525a5081a920062b883644dc8f5734bcc6806bb.img",
  "recovery_len": 15926572,
  "recovery_hash": "db31ffe79dfd60be966fba6d1525a5081a920062b883644dc8f5734bcc6806bb"
}

So, this is an attempt to create a URL that I can replace in download.py, line 17, 
from:
RELEASE_MANIFEST = "https://raw.githubusercontent.com/commaai/openpilot/release2/installer/updater/update.json"
to:
