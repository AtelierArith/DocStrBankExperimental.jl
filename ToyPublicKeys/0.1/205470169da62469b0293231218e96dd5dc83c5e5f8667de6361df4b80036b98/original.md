```
decrypt(::pkcs1_v2_2_t,
        msg::Vector{UInt8},
        key::RSAPrivateKey)
```

RSA decryption function, expects [PKCS#1 v2.2](https://www.rfc-editor.org/rfc/rfc8017.html#page-19).
