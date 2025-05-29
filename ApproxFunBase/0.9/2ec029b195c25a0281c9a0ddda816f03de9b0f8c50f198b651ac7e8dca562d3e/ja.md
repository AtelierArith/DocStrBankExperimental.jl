```
transform(s::Space, vals)
```

指定されたグリッド `points(s,length(vals))` 上の値を空間 `s` の係数に変換します。デフォルトでは `coefficients(transform(canonicalspace(space),values),canonicalspace(space),space)` です。

# 例

```jldoctest
julia> F = Fun(x -> x^2, Chebyshev());

julia> coefficients(F)
3-element Vector{Float64}:
 0.5
 0.0
 0.5

julia> transform(Chebyshev(), values(F)) ≈ coefficients(F)
true

julia> v = map(F, points(Chebyshev(), 4)); # カスタムグリッド

julia> transform(Chebyshev(), v)
4-element Vector{Float64}:
 0.5
 0.0
 0.5
 0.0
```
