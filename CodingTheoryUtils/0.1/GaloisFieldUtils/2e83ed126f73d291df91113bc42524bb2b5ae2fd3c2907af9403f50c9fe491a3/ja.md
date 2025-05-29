```
gf_pretty(v::Vector{F}, α::F)::Vector{String} where F <: GaloisFields.AbstractGaloisField
```

ガロア体の要素のベクトルを `gf_pretty(a, α)` を使用して各要素を整形して表示します。

# 引数

  * `v::Vector{F}`: ガロア体の要素のベクトル。
  * `α::F`: フィールドの原始要素。

# 戻り値

  * `Vector{String}`: 文字列表現のベクトル。
