```
field_size(a::GaloisFields.AbstractGaloisField)::Int
```

有限体のサイズを計算します。

# 引数

  * `a::GaloisFields.AbstractGaloisField`: 有限体の要素

# 戻り値

  * 有限体のサイズ

# 例

```julia
F4, α = GaloisField(2, 2, :α)
field_size(α) == 4
```
