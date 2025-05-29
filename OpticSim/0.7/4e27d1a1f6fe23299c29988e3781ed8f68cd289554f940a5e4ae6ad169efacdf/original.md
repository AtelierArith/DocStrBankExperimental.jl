```
BezierCurve{P,S,N,M} <: Spline{P,S,N,M}
```

`N` is the dimension of the curve, `M` is the curve order

```julia
BezierCurve{P,S,N,M}(controlpoints::AbstractArray{<:AbstractArray{S,1},1})
```
