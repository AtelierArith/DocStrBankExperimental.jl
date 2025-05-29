```
coefficients(f::Fun) -> Vector
```

Return the coefficients of `f`, corresponding to the space `space(f)`.

# Examples

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> coefficients(f)
3-element Vector{Float64}:
 0.5
 0.0
 0.5
```
