```julia
decrypt_vigenere(ciphertext, key::Array)
decrypt_vigenere(plaintext, key::AbstractString)
```

与えられたオフセットのベクトルに従って、Vigenere暗号を使用して指定された文字列を復号化します。たとえば、`decrypt_vigenere("ac", [0, 1])`は`"ab"`を返します。

---

### 例

```julia
julia> decrypt_vigenere("HFLMOXOSLE", [0, 1]) # オフセット`0`はキー`a`に対応することに注意してください。
"helloworld"
```
