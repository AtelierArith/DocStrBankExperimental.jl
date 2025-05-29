```
LaurentRight(p::Polynomial)
```

Shifts polynomial `p` to the right.

# Examples

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2 

julia> LaurentRight(p)
z^-3 + 2*z^-2 + 3*z^-1 + 4 + 5*z
```
