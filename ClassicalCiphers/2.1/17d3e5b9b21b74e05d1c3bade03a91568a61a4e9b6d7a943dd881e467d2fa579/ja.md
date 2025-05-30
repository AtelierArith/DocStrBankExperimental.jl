```julia
decrypt_atbash(ciphertext, alphabet)
```

置換暗号の特別なケースであるアトバッシュ暗号は、与えられたアルファベットをその逆に置き換えます：

```julia
decrypt_atbash(ciphertext, "abcdefghijklmnopqrstuvwxyz") == decrypt_substitution(ciphertext, "zyxwvutsrqponmlkjihgfedcba", "abcdefghijklmnopqrstuvwxyz")
decrypt_atbash(ciphertext, "abcdefghijklmnopqrstuvwxyz") == decrypt_substitution(ciphertext, "zyxwvutsrqponmlkjihgfedcba"; reverse_dict = true)
```

*アルファベットを省略すると、英語のアルファベットを使用していると見なされます。*

---

### 例

```julia
julia> encrypt_atbash("some text", "abcdefghijklmnopqrstuvwxyz")
"HLNV GVCG"

julia> decrypt_atbash("HLNV GVCG", "abcdefghijklmnopqrstuvwxyz")
"some text"
```
