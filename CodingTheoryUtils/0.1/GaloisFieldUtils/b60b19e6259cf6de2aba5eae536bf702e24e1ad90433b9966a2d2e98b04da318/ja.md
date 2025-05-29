```
gf_pretty(a::F, α::F)::String where F <: GaloisFields.AbstractGaloisField
```

ガロア体の要素を "α^p" の形式で整形して表示します。

# 引数

  * `a::F`: 表示するガロア体の要素。
  * `α::F`: 基準として使用される体の原始要素。

# 戻り値

  * `String`: "α^p" の文字列表現、または要素がゼロの場合は "0"。

# 例

```julia
F4, α = GaloisField(4, :α)
gf_pretty(α, α) == "α^1"
gf_pretty(F4(1), α) == "α^0"
gf_pretty(F4(0), α) == "0"
```
