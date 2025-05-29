```
itransform(s::Space,coefficients::AbstractVector)
```

Transform coefficients back to values.  Defaults to using `canonicalspace` as in `transform`.

# Examples

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
