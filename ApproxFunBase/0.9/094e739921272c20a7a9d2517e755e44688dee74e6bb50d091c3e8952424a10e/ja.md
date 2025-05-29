```
itransform(s::Space,coefficients::AbstractVector)
```

係数を値に戻します。デフォルトでは、`transform`と同様に`canonicalspace`を使用します。

# 例

```jldoctest
julia> F = Fun(x->x^2, Chebyshev())
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> itransform(Chebyshev(), coefficients(F)) ≈ values(F)
true

julia> itransform(Chebyshev(), [0.5, 0, 0.5])
3-element Vector{Float64}:
 0.75
 0.0
 0.75
```
