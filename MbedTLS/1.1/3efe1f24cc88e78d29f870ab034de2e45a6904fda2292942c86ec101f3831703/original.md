`Cipher(info::Union{CipherID, CipherKind}) -> Cipher`

Construct a cipher object and set it to use the specified cipher algorithm.

The algorithm can either be specific (ie, `CIPHER_AES_256_CBC`), or general (ie, `CIPHER_AES`). In the latter case, a default choice of specific cipher will be used. See `?CipherInfo` for more details.
