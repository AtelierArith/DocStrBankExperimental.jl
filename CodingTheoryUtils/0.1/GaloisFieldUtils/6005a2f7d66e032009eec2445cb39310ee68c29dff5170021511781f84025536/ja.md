```
get_minimum_polynomial(β::F)::Polynomial{F} where F <: GaloisFields.AbstractExtensionField
```

有限体の要素の最小多項式を計算します。

# 引数

  * `β`: 有限体の要素

# 戻り値

  * `Polynomial{F}`: 要素の最小多項式

# 例

```julia
julia> F4 = @GaloisField 2^2
julia> α = primitiveroot(F4)
julia> get_minimum_polynomial(α)
Polynomial(1 + x + x^2)
```
