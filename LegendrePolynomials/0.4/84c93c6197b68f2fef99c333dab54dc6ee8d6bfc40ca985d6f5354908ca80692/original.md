```
collectdnPl(x; lmax::Integer, n::Integer)
```

Compute the $n$-th derivative of a Legendre Polynomial $P_\ell(x)$ for the argument `x` and all degrees `l = 0:lmax`.

The order of the derivative `n` must be greater than or equal to zero.

Returns `v` with indices `0:lmax`, where `v[l] == dnPl(x, l, n)`.

# Examples

```jldoctest
julia> collectdnPl(0.5, lmax = 3, n = 2)
4-element OffsetArray(::Vector{Float64}, 0:3) with eltype Float64 with indices 0:3:
 0.0
 0.0
 3.0
 7.5
```
