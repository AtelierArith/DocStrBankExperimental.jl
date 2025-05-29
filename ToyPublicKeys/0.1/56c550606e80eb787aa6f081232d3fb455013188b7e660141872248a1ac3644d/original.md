```
encrypt(::pkcs1_v1_5_t,
        msg::Vector{UInt8},
        key::RSAPublicKey)
```

RSA encryption function with [PKCS#1 v1.5](https://www.rfc-editor.org/rfc/rfc2313#section-8.1).
