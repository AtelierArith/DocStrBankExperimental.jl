```
dnPl(x, l::Integer, n::Integer, [cache::AbstractVector])
```

Compute the $n$-th derivative $d^n P_\ell(x)/dx^n$ of the Legendre polynomial $P_\ell(x)$. Optionally a pre-allocated vector `cache` may be provided, which must have a minimum length of `l - n + 1` and may be overwritten during the computation.

The order of the derivative `n` must be non-negative. For `n == 0` this function just returns Legendre polynomials.

# Examples

```jldoctest
julia> dnPl(0.5, 3, 2) # second derivative of P3(x) at x = 0.5
7.5

julia> dnPl(0.5, 4, 0) == Pl(0.5, 4) # zero-th order derivative == Pl(x)
true
```
