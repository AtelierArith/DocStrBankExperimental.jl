```
verify_signature(::pkcs1_v1_5_t,
                 msg::Vector{UInt8},
                 signature::Vector{UInt8},
                 key::RSAPublicKey)
```

Verify the signature by [PKCS#1 v1.5](https://www.rfc-editor.org/rfc/rfc2313.txt)
