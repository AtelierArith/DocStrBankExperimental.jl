```
verify_signature(msg::Vector{UInt8},
                 signature::Vector{UInt8},
                 key::RSAPublicKey)
```

Verify the signature by [PKCS#1 v2.2](https://www.rfc-editor.org/rfc/rfc8017.html#page-19)
