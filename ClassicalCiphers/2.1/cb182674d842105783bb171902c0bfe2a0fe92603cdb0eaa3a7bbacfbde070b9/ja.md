```julia
encrypt_portas(plaintext, key_in::AbstractString)
```

ポルタス暗号を使用して、指定された平文を暗号化します。

キーは文字列として与えられ、文字はアルファベットでなければなりません。

テキストを大文字に変換します。

---

### 例

```julia
julia> encrypt_portas("Hello, World!", "ab")
"URYYB, JBEYQ!"
```
