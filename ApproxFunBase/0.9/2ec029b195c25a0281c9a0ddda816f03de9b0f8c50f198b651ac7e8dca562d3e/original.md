```
transform(s::Space, vals)
```

Transform values on the grid specified by `points(s,length(vals))` to coefficients in the space `s`. Defaults to `coefficients(transform(canonicalspace(space),values),canonicalspace(space),space)`

# Examples

```jldoctest
julia> F = Fun(x -> x^2, Chebyshev());

julia> coefficients(F)
3-element Vector{Float64}:
 0.5
 0.0
 0.5

julia> transform(Chebyshev(), values(F)) ≈ coefficients(F)
true

julia> v = map(F, points(Chebyshev(), 4)); # custom grid

julia> transform(Chebyshev(), v)
4-element Vector{Float64}:
 0.5
 0.0
 0.5
 0.0
```
