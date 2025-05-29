```
collectPl(x; lmax::Integer, [lmin::Integer = 0], [kwargs...])
```

Compute the Legendre Polynomial $P_\ell(x)$ for the argument `x` and degrees `l = lmin:lmax`. Return `P` with indices `lmin:lmax`, where `P[l] == Pl(x, l; kwargs...)`

# Optional keyword arguments

  * `norm`: The normalization used in the function. Possible   options are `Val(:standard)` (default) and `Val(:normalized)`.   The functions obtained with `norm = Val(:normalized)` have an L2 norm of $1$.

# Examples

```jldoctest
julia> v = collectPl(0.5, lmax = 4);

julia> all(l -> v[l] ≈ Pl(0.5, l), 0:4)
true

julia> v = collectPl(0.5, lmax = 4, norm = Val(:normalized));

julia> all(l -> v[l] ≈ Pl(0.5, l, norm = Val(:normalized)), 0:4)
true
```
