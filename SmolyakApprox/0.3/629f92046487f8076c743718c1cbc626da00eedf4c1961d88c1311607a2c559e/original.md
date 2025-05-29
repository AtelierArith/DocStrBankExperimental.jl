Computes `N` uniformly spaced points of floating point type `T` on [1.0,-1.0] and scales the points to the interval given in `domain` (defaults to [1.0,-1.0]).  Returns a vector containing the `N` points located  over the specified domain.

# Signature

points = clenshaw*curtis*equidistant(T,N,domain)

# Examples

```
julia> using DoubleFloats
julia> points = clenshaw_curtis_equidistant(Double64,4)
[-1.0
 -0.33333333333333337
  0.33333333333333337
  1.0]

julia> points = clenshaw_curtis_equidistant(Double64,4,[3.0,-1.0])
[-1.0
  0.33333333333333326
  1.6666666666666667
  3.0]

  julia> points = clenshaw_curtis_equidistant(BigFloat,4,[3.0,-1.0])
[-1.0
  0.3333333333333332593184650249895639717578887939453125
  1.6666666666666667406815349750104360282421112060546875
  3.0]
```
