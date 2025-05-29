```
Pl(x, l::Integer; [norm = Val(:standard)])
```

Compute the Legendre Polynomial $P_\ell(x)$ for the argument `x` and the degree `l`.

The default norm is chosen to be `Val(:standard)`, in which case the polynomials satisfy `Pl(1, l) == 1` for all `l`. Optionally, the `norm` may be set to `Val(:normalized)` to obtain normalized Legendre polynomials. These have an L2 norm of `1`.

# Examples

```jldoctest
julia> Pl(1, 2)
1.0

julia> Pl(0.5, 4) ≈ -37/128 # analytically obtained value
true

julia> Pl(0.5, 20, norm = Val(:normalized))
-0.21895188261094017
```
