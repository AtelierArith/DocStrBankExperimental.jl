```
LaurentDown(p::Polynomial)
```

Downscales p.

# Examples

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2 

julia> LaurentDown(p)
z^-1 + 3.0 + 5.0*z
```
