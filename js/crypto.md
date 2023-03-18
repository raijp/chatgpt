```
const fc = (() => {
  const xorKey = 0x81; // 10000001
  const encodeDecode = (str) => {
    const encoder = new TextEncoder();
    const decoder = new TextDecoder();
    const encodedData = encoder.encode(str);
    const xorData = new Uint8Array(encodedData.length);
    for (let i = 0; i < encodedData.length; i++) {
      xorData[i] = encodedData[i] ^ xorKey;
    }
    return decoder.decode(xorData);
  };
  const encrypt = (originalText) => encodeURIComponent(encodeDecode(originalText));
  const decrypt = (encryptedText) => encodeDecode(decodeURIComponent(encryptedText));
  return { encrypt, decrypt };
})();
```
