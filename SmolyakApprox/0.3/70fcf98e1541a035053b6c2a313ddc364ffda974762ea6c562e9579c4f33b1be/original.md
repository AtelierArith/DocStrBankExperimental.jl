Computes `N` uniformly spaced points on [1.0,-1.0] and scales the points to the interval given in `domain` (defaults to [1.0,-1.0]).  Returns a vector containing the `N` points located over the specified domain.

clenshaw-Curtis equidistant points are used in the case where the Smolyak approximation is based on piecewise linear basis functions.

# Signature

points = clenshaw*curtis*equidistant(N,domain)

# Examples

```
julia> points = clenshaw_curtis_equidistant(4)
[-1.0
 -0.33333333333333337
  0.3333333333333335
  1.0]

julia> points = clenshaw_curtis_equidistant(4,[3.0,-1.0])
[-1.0
  0.33333333333333326
  1.666666666666667
  3.0]
```
