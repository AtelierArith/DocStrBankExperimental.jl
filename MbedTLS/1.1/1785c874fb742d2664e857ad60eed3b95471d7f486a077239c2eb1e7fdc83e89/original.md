`decrypt(cipher, key, msg, [iv]) -> Vector{UInt8}`

Decrypt a message using the given cipher. The cipher can be specified as

  * a generic cipher (like CIPHER_AES)
  * a specific cipher (like CIPHER*AES*256_CBC)
  * a Cipher object

`key` is the symmetric key used for cryptography, given as either a String or a `Vector{UInt8}`. It must be the right length for the chosen cipher; for example, CIPHER*AES*256_CBC requires a 32-byte (256-bit) key.

`msg` is the message to be encoded. It should either be convertible to a String or be a `Vector{UInt8}`.

`iv` is the initialization vector, whose size must match the block size of the cipher (eg, 16 bytes for AES) and correspond to the iv used by the encryptor. By default, it will be set to all zeros.
