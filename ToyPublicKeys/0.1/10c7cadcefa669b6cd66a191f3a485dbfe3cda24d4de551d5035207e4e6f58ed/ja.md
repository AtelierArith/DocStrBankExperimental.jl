```
sign(::pkcs1_v1_5_t,
     msg::Vector{UInt8},
     key::RSAPrivateKey)
```

RSAキーを使用して文字列に署名します [PKCS#1 v1.5](https://www.rfc-editor.org/rfc/rfc2313.txt)
