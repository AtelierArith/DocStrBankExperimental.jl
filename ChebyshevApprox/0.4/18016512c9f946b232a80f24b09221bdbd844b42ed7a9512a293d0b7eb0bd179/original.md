Computes `N` Chebyshev extended points and scales the points to the interval given in `domain` (defaults to [1.0,-1.0]).  Returns a vector containing the `N` Chebyshev extended points located over the specified domain.

# Signature

points = chebyshev_extended(N,domain)

# Examples

```
julia> points = chebyshev_extended(4)
[-1.0
 -0.41421356237309515
  0.41421356237309515
  1.0]

julia> points = chebyshev_extended(4,[3.0,-1.0])
[-1.0
  0.1715728752538097
  1.8284271247461903
  3.0]
```
