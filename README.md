<p align="center">
  <img alt="OS.js Logo" src="https://raw.githubusercontent.com/os-js/gfx/master/logo-big.png" />
</p>

[OS.js](https://www.os-js.org/) is an [open-source](https://raw.githubusercontent.com/os-js/OS.js/master/LICENSE) desktop implementation for your browser with a fully-fledged window manager, Application APIs, GUI toolkits and filesystem abstraction.

[![Community](https://img.shields.io/badge/join-community-green.svg)](https://community.os-js.org/)
[![Donate](https://img.shields.io/badge/liberapay-donate-yellowgreen.svg)](https://liberapay.com/os-js/)
[![Donate](https://img.shields.io/badge/paypal-donate-yellow.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=andersevenrud%40gmail%2ecom&lc=NO&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donate_SM%2egif%3aNonHosted)
[![Support](https://img.shields.io/badge/patreon-support-orange.svg)](https://www.patreon.com/user?u=2978551&ty=h&u=2978551)

# OS.js v3 WebDAV VFS Adapter

This is the WebDAV VFS (Server) Adapter for OS.js v3.

## Installation

```
const webdavAdapter = require('@osjs/webdav-adapter');

osjs.register(VFSServiceProvider, {
  depends: ['osjs/gapi'],
  args: {
    adapters: {
      webdav: webdavAdapter
    }
  }
});
```

Then create a mountpoint. Example using ownCloud:

```
// src/server/config.js
{
  vfs: {
    mountpoints: [{
      name: 'owncloud',
      label: 'ownCloud',
      adapter: 'owncloud',
      attributes: {
        connection: {
          uri: 'http://localhost:8002',
          username: 'osjs',
          password: 'osjs',
          access_token: null,
          prefix: '/remote.php/webdav'
        }
      }
     }]
   }
}

// src/client/config.js
{
  vfs: {
    mountpoints: [{
      name: 'owncloud',
      label: 'ownCloud'
     }]
   }
}
```

*At some point users can create their own server mounts via the client*.
