```
encrypt(::pkcs1_v1_5_t,
        msg::Vector{UInt8},
        key::RSAPublicKey)
```

RSA暗号化関数 [PKCS#1 v1.5](https://www.rfc-editor.org/rfc/rfc2313#section-8.1)。
