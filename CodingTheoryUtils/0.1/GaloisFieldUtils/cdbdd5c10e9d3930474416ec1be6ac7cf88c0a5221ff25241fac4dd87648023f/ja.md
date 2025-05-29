```
extension_degree(a::GaloisFields.AbstractGaloisField)::Int
```

有限体の拡張次数を計算します。

# 引数

  * `a::GaloisFields.AbstractGaloisField`: 有限体の要素

# 戻り値

  * 有限体の拡張次数

# 例

```julia
F4, α = GaloisField(2, 2, :α)
extension_degree(α) == 2
```
