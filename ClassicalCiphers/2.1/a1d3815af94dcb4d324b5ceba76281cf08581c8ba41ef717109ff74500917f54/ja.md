```julia
decrypt_playfair(ciphertext, key::Array{Char, 2}; combined::AbstractPair{Char, Char} = ('I', 'J'))
```

与えられた暗号文をプレイフェア暗号に従って復号します。

ダブルレターのために挿入されたXを削除しようとはしません。

---

### 例

```julia
julia> decrypt_playfair("RMRMFWYE", "playfair example")
"ixixyzax"
```
