```
get_order(x::F) where F <: GaloisFields.AbstractGaloisField
```

有限体の要素の位数を計算します。

# 引数

  * `x::F`: 有限体の要素

# 戻り値

  * `Int`: 要素の位数。要素がゼロの場合は -1 を返します。

# 例

```julia
F4, α = GaloisField(2, 2, :α)
get_order(α)  # 3
get_order(F4(1))  # 1
get_order(F4(0))  # -1
```
