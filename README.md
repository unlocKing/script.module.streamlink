# script.module.streamlink

## Download

- https://github.com/back-to/repo
- https://github.com/back-to/repo/raw/master/repository.back-to/repository.back-to-5.0.0.zip

## Support

- LiveProxy
  https://github.com/back-to/liveproxy

- Custom Plugins
  https://github.com/back-to/plugins

- Default Plugins
  https://github.com/streamlink/streamlink

# script.module.pycryptodome

Only **Kodi Leia** has `script.module.pycryptodome` **prepacked**.

If you want to use this plugin on **Krypton**,

you will have to install [pycryptodome](https://github.com/Legrandin/pycryptodome#pycryptodome) on **your system**
and create a **dummy** `script.module.pycryptodome` plugin.

# Guide

## How to use this libary with Kodi?

**Kodi Leia** has pycryptodomex **prepacked**,
but streamlink only supports pycryptodome.

You will have to rename the **Cryptodome** package into **Crypto**

Add this to your **main** class

```py
import sys
try:
    import Cryptodome
    sys.modules['Crypto'] = Cryptodome
except ImportError:
    # Cryptodome is not installed,
    # but Crypto might be installed
    pass
```

After this everything from the Streamlink API should work.

https://streamlink.github.io/api_guide.html

## How to rebuild this Kodi-Addon?

It's not automated yet ...

- remove the `resources/lib/streamlink` folder
- create a `bdist` or `wheel` of streamlink
- from the `bdist` unpack the `streamlink` folder to the empty `resources/lib/streamlink`
- if you use a git folder, run `git add .`
- run `python replace.py`
- if you use a git folder, inspect the changes `git status`
- update `addon.xml`
- zip the folder
