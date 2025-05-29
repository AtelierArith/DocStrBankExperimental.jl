```
LaurentLeft(p::Polynomial)
```

Shifts polynomial `p` to the left.

# Examples

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2 

julia> LaurentLeft(p)
z^-1 + 2 + 3*z + 4*z^2 + 5*z^3 
```
