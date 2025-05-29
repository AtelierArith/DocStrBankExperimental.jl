```
collectdnPl!(v::AbstractVector, x; lmax::Integer, n::Integer)
```

Compute the $n$-th derivative of a Legendre Polynomial $P_\ell(x)$ for the argument `x` and all degrees `l = 0:lmax`, and store the result in `v`.

The order of the derivative `n` must be greater than or equal to zero.

At output, `v[l + firstindex(v)] == dnPl(x, l, n)` for `l = 0:lmax`.

# Examples

```jldoctest
julia> v = zeros(4);

julia> collectdnPl!(v, 0.5, lmax = 3, n = 2)
4-element Vector{Float64}:
 0.0
 0.0
 3.0
 7.5
```
