```
extension_degree(ff::Type{<:GaloisFields.AbstractGaloisField})::Int
```

有限体の拡張次数を計算します。

# 引数

  * `ff::Type{<:GaloisFields.AbstractGaloisField}`: 有限体の型

# 戻り値

  * 有限体の拡張次数

# 例

```julia
F4, α = GaloisField(2, 2, :α)
extension_degree(F4) == 2

GF2 = GaloisField(2)
extension_degree(GF2) == 1
```
