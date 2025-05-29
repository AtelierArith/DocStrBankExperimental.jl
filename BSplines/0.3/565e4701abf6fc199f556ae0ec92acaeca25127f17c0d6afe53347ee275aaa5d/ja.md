```
breakpoints(basis::BSplineBasis)
```

Bスプライン基底のブレークポイント列を返します。

# 例

```jldoctest
julia> breakpoints(BSplineBasis(3, 0:5))
0:5

julia> breakpoints(BSplineBasis(4, [1.0, 1.5, 2.5, 4.0]))
4-element Vector{Float64}:
 1.0
 1.5
 2.5
 4.0
```
