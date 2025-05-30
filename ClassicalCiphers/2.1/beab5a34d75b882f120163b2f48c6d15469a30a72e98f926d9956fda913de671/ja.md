```julia
encrypt_vigenere(plaintext, key::Array)
encrypt_vigenere(ciphertext, key::AbstractString)
```

与えられたオフセットのベクトルに従って、Vigenere暗号を使用して指定された文字列を暗号化します。たとえば、`encrypt_vigenere("ab", [0, 1])`は`"AC"`を返します。

---

### 例

```julia
julia> encrypt_vigenere("Hello, World!", "ab")
"HFLMOXOSLE"
```
