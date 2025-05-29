```julia
(a,b) = linreg(x::AbstractVector, y::AbstractVector)
```

`y = a + bx` の形の単純な線形最小二乗回帰の係数を返します。

### 例

```
julia> a, b = linreg(1:10, 1:10)
2-element Vector{Float64}:
 -1.19542133983862e-15
  1.0

julia> isapprox(a, 0, atol = 1e-12)
true

julia> isapprox(b, 1, atol = 1e-12)
true
```
