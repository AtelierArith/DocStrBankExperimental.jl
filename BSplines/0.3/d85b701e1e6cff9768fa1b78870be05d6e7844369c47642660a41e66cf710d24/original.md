```
averagebasis(order, datapoints) -> BSplineBasis
```

Returns a B-spline basis with the specified `order` that is well-suited for interpolation on the given `datapoints`. The `datapoints` vector is assumed to be sorted.

The calculated breakpoints are described in [^deBoor1978], p. 219, as a “reasonable alternative” to the optimal breakpoint sequence since they are “often very close to the optimum” and are computationally inexpensive.

[^deBoor1978]: Carl de Boor, *A Practical Guide to Splines*, New York, N.Y.: Springer, 1978.

# Examples

```jldoctest
julia> averagebasis(5, 0:10)
11-element BSplines.BSplineBasis{Vector{Float64}}:
 order: 5
 breakpoints: [0.0, 2.5, 3.5, 4.5, 5.5, 6.5, 7.5, 10.0]
```
