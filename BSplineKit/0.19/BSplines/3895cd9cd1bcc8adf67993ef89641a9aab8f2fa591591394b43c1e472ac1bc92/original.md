```
getindex(B::AbstractBSplineBasis, i, [T = Float64])
```

Get $i$-th basis function.

This is an alias for `BasisFunction(B, i, T)` (see [`BasisFunction`](@ref) for details).

The returned object can be evaluated at any point within the boundaries defined by the basis.

# Examples

```jldoctest
julia> B = BSplineBasis(BSplineOrder(4), -1:0.1:1)
23-element BSplineBasis of order 4, domain [-1.0, 1.0]
 knots: [-1.0, -1.0, -1.0, -1.0, -0.9, -0.8, -0.7, -0.6, -0.5, -0.4  …  0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1.0, 1.0, 1.0, 1.0]

julia> B[6]
Basis function i = 6
  from 23-element BSplineBasis of order 4, domain [-1.0, 1.0]
  support: [-0.8, -0.4) (knots 6:10)

julia> B[6](-0.5)
0.16666666666666666

julia> B[6, Float32](-0.5)
0.16666667f0

julia> B[6](-0.5, Derivative(1))
-5.000000000000001
```
