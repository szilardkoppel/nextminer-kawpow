# NextMiner Kawpow

This is a Node module for simple hashing and verifying inputs using the
KawPOW proof-of-work algorithm as implemented by [Ravencoin](https://github.com/RavenProject/Ravencoin/releases/tag/v4.0.0). Most of the native code comes from or is adapted from [Ravencoin code](https://github.com/RavenProject/Ravencoin). This module has been developed and tested on [Node v10.16.3](https://nodejs.org/) and
[Ubuntu 16.04](http://releases.ubuntu.com/16.04/).

#### Need Support?

If you need help with a code-related matter, the first place to look is our [Discord](https://discord.gg/SzeBuNQp), where the developers will be available to answer any questions. However, please do not come to me with issues regarding setup. Use Google and the existing documentation for that.

---

### Install & Test

```bash
curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
sudo apt-get install nodejs -y
sudo apt-get install build-essential
git clone https://github.com/szilardkoppel/nextminer-kawpow.git
cd nextminer-kawpow
npm install && npm test
```

---

### Usage

```javascript
const kawpow = require('nextminer-kawpow');
const mixOutBuf = Buffer.alloc(32);
const hashOutBuf = Buffer.alloc(32);

/**
 * Hash using a single nonce and place results into the specified output Buffers.
 *
 * Note that all input values are expected to be in little-endian format.
 *
 * All output values are in little endian format
 *
 * @param headerHashBuf {Buffer} 32-byte header hash
 * @param nonceBuf {Buffer} 8-byte nonce value (64-bits)
 * @param blockHeight {number} Block height integer
 * @param mixOutBuf {Buffer} Mix hash result output Buffer
 * @param hashOutBuf {Buffer} Hash result output Buffer
 */

kawpow.hashOne(headerHashBuf, nonceBuf, blockHeight, mixOutBuf, hashOutBuf);

console.log(mixHashBuf.toString('hex'));
console.log(hashOutBuf.toString('hex'));
```

```javascript
const kawpow = require('nextminer-kawpow');
const hashValueOut = Buffer.alloc(32);

/**
 * Verify a mix hash.
 *
 * Note that all input values are expected to be in little-endian format.
 *
 * All output values are in little endian format.
 *
 * @param headerHashBuf {Buffer} 32-byte header hash
 * @param nonceBuf {Buffer} 8-byte nonce value (64-bits)
 * @param blockHeight {number} Block height integer
 * @param mixHashBuf {Buffer} Mix hash for verification
 * @param hashOutBuf {Buffer} Hash result output Buffer
 * @returns {boolean} True if valid, otherwise false.
 */

const isValid = kawpow.verify(headerHashBuf, nonceBuf, blockHeight, mixHashBuf, hashValueOut);

if (isValid) {
    console.log(hashValueOut.toString('hex'));
}
else {
    console.log('Invalid');
}
```

---

### Donations

Maintaining this project has always been driven out of nothing more than a desire to give back to the mining community, however I always appreciate donations, especially if this repository helps you in any way.

- Bitcoin:         3EbrVYLxN5WeQmPpL6owo3A7rJELXecbbc
- Ethereum:        0x164eebCc2F626E3B9EED622E7928554452CFBe1c
- EtheriumClassic: 0xAd6DF90A14F1e6Bc07289e7E63BF6Faf28ef325A
- Raven:           RGCivyubfCJJ3ZabAGpRNCcRGrPoqVsawW
- Ergo:            9hs8Lg44Gnv55XWyY7giUiWuNxpSNRrmVsSZsuvXanFRPsPEgKF

---

### License

Released under the MIT License. See https://opensource.org/licenses/MIT for more information

---