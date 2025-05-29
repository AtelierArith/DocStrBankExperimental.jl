Computes `N` roots of the Chebyshev polynomial and scales the roots to the interval given in `domain` (defaults to [1.0,-1.0]).  Returns a vector containing the `N` Chebyshev roots located over the specified domain.

# Signature

points = chebyshev_nodes(N,domain)

# Examples

```
julia> points = chebyshev_nodes(2)
[-0.7071067811865476
  0.7071067811865476]

julia> points = chebyshev_nodes(2,[3.0,-1.0])
[-0.41421356237309515
  2.414213562373095]
```
