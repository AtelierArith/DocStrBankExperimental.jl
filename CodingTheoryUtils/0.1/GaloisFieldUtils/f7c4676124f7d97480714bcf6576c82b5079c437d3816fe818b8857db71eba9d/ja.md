```
field_size(FF::Type{<:GaloisFields.AbstractGaloisField})::Int
```

有限体のサイズを計算します。

# 引数

  * `FF::Type{<:GaloisFields.AbstractGaloisField}`: 有限体の型

# 戻り値

  * 有限体のサイズ

# 例

```julia
F4, α = GaloisField(2, 2, :α)
field_size(F4) == 4
```
