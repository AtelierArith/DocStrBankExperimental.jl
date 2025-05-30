```julia
decrypt_hill(ciphertext, key::AbstractArray{T, 2}) where {T <: Integer}
```

---

### 例

```julia
julia> decrypt_hill("PLHCGQWHRY", [1 2; 5 7]) # 鍵 `[1 2; 5 7]` を使ってテキスト "PLHCGQWHRY" を復号化する
"helloworld"

julia> decrypt_hill("PLHCGQWHRY", "bcfh")
"helloworld"

julia> decrypt_hill("PLHCIX", "bcfh") # 平文の長さが鍵行列の次元の倍数でない場合、Xでパディングされる
"hellox"
```
