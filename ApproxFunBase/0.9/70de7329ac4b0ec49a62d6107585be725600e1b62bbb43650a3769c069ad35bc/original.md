```
space(f::Fun)
```

Return the space of `f`.

# Examples

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> space(f)
Chebyshev()
```
