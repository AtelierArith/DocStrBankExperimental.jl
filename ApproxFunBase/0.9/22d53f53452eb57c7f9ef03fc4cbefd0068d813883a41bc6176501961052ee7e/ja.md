```
coefficients(f::Fun) -> Vector
```

`f`の係数を返します。これは`space(f)`に対応します。

# 例

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> coefficients(f)
3-element Vector{Float64}:
 0.5
 0.0
 0.5
```
