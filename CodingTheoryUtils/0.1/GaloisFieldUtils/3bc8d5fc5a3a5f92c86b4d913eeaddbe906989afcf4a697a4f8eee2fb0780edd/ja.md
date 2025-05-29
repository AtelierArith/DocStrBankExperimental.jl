```
get_roots(px::Polynomial{F})::Array{F,1} where F <: GaloisFields.AbstractExtensionField
```

有限体上の多項式の根を計算します。

# 引数

  * `px`: 有限体上の多項式

# 戻り値

  * `Array{F,1}`: 多項式の根の配列

# 例

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> p = Polynomial([F4(1), F4(1), F4(1)])  # x^2 + x + 1
julia> get_roots(p)
2-element Array{GaloisField{2,2},1}:
 α
 α^2
```
