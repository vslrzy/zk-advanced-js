# zk-advanced-js

An improved and extended version of [zkteco-js](https://www.npmjs.com/package/zkteco-js) (original repo: [coding-libs/zkteco-js](https://github.com/coding-libs/zkteco-js))

Repository: https://github.com/vslrzy/zk-advanced-js  
Maintained by: vslrzy

## Changes & Improvements

- Added device-level methods for enrolling and managing fingerprints by **specific user ID** and **finger index**.
- Implemented controlled **startEroll** process that waits for user input and tracks success or failure.
- Built-in **timeout** handling for enroll operations (no more hanging connections).
- Added **enroll result detection**, reporting clear success or failure states.
- Added ability to **delete a specific finger** of a user directly from the device.

## New / Advanced Functionality

> These helpers simplify real-time device interaction for enrollment, timeout control, and selective deletion.

- **Start enroll for selected user & finger index**

  - `startEroll(userId, fingerIndex, timeout)`
  - Wakes the device and waits for a finger to be enrolled for the specified user and finger index.

- **Timeout-based enroll waiting**

  - Automatically stops waiting after the configured timeout period.

- **Enroll success/failure detection**

  - Detects whether the enroll process completed successfully or failed due to poor capture, mismatch.

- **Delete user finger**
  - `deleteFingerprintTemplate(userId, fingerIndex)`
  - Removes a single finger template for the given user directly from the device.

## Example usage

```js
const Zkteco = require("zkteco-js");

const manageZktecoDevice = async () => {
  const device = new Zkteco("192.168.1.106", 4370, 5200, 5000);

  try {
    // Create socket connection to the device
    await device.createSocket();

    // Start enroll by uid, finger index, timeout
    await device.startEnroll(1, 3, 5000);

    // Delete fingerprint template by uid, finger index
    await device.deleteFingerprintTemplate(1, 3);
  } catch (error) {
    console.error("Error:", error);
  }
};

manageZktecoDevice();
```

---

[![Buy me a coffee](https://img.shields.io/badge/Buy%20me%20a%20coffee-☕-FFDD00)](https://buymeacoffee.com/vslrzy)

If this project saved you time, consider buying me a coffee: https://buymeacoffee.com/vslrzy — much appreciated ☕
