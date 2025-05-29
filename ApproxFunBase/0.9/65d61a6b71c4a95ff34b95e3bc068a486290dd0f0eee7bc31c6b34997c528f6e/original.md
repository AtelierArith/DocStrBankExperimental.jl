```
extrapolate(f::Fun,x)
```

Return an extrapolation of `f` from its domain to `x`.

# Examples

```jldoctest
julia> f = Fun(x->x^2)
Fun(Chebyshev(), [0.5, 0.0, 0.5])

julia> extrapolate(f, 2) # 2 lies outside the domain -1..1
4.0
```
