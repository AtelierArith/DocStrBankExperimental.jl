```
KnotVector(ζs::Vector{Float64}, nel::Int64, poly::Int64, curve::Curve)
```

Vector of knots, with which all 1-D B-spline functions are calculated.

The knot vector struct contains four fields:

  * `ζs` –> list of all knots, including repeated ones
  * `nel` –> number of 1-D elements, or knot spans
  * `poly` –> polynomial order
  * `curve` –> type of [Curve](@ref), which is either `CLAMPED` or `CLOSED`

All of these data are not required to generate a knot vector. Two constructors are available—see [knot_vector](@ref)
