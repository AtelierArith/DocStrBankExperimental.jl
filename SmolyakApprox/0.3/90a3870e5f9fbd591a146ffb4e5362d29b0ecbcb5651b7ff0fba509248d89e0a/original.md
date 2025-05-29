Computes `N` Chebyshev-Gauss-Lobatto (Chebyshev extrema) and scales the points to the interval given in `domain` (defaults to [1.0,-1.0]).  Returns a vector containing the `N` points located over the  specified domain.

Chebyshev-Gauss-Lobatto points are used in the case where the Smolyak approximation is based on Chebyshev polynomials.

# Signatures

points = chebyshev*gauss*lobatto(N,domain) points = chebyshev_extrema(N,domain)

# Examples

```
julia> points = chebyshev_gauss_lobatto(4)
[-1.0
 -0.5000000000000001
  0.5000000000000001
  1.0]

julia> points = chebyshev_gauss_lobatto(4,[3.0,-1.0])
[-1.0
 -2.220446049250313e-16
  2.0
  3.0]
```
