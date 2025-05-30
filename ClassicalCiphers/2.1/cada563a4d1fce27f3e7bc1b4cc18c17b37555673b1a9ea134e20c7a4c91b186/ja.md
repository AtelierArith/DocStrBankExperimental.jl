```julia
decrypt_portas(ciphertext, key::AbstractString)
```

ポータス暗号を使用して、与えられた暗号文を復号化します。

キーは文字列として与えられ、文字はアルファベットでなければなりません。

テキストを小文字に変換します。

---

### 例

```julia
julia> decrypt_portas("URYYB, JBEYQ!", "ab")
"hello, world!"
```
