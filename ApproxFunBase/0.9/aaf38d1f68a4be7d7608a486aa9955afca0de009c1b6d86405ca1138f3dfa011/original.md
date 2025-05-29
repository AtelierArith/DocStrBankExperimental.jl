```
ncoefficients(f::Fun) -> Integer
```

Return the number of coefficients of a fun

# Examples

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> ncoefficients(f)
3
```
