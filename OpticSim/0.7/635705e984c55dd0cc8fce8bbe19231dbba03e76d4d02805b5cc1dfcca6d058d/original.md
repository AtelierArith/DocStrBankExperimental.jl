```
BSplineCurve{P,S,N,M} <: Spline{P,S,N,M}
```

`N` is the spatial dimension of the curve. `M` is the curve order, i.e., the highest power of the parameterizing variable, `u`. All curve segments are assumed to be of the same order.

```julia
BSplineCurve{P,S,N,M}(knots::KnotVector{S}, controlpoints::AbstractArray{MVector{N,S},1})
```
