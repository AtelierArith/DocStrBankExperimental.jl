```
values(f::Fun)
```

Return `f` evaluated at `points(f)`.

# Examples

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> values(f)
3-element Vector{Float64}:
 0.75
 0.0
 0.75

julia> map(x->x^2, points(f)) ≈ values(f)
true
```
