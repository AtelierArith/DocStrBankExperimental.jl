Computes `N` extrema of the Chebyshev polynomial and scales the extrema to the interval given in `domain`  (defaults to [1.0,-1.0]).  Returns a vector containing the `N` Chebyshev extrema located over the specified  domain.

# Signature

points = chebyshev_extrema(N,domain)

# Examples

```
julia> points = chebyshev_extrema(4)
[-1.0
 -0.5000000000000001
  0.5000000000000001
  1.0]

julia> points = chebyshev_extrema(4,[3.0,-1.0])
[-1.0
 -2.220446049250313e-16
  2.0
  3.0]
```
