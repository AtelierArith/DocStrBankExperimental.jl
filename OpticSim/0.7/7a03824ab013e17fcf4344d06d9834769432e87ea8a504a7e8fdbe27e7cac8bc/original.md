```
Spline{P<:CurveType,S<:Number,N,M}
```

`M` is the curve order, i.e., the highest power of the parameterizing variable, u. `P` determines the [`CurveType`](@ref).

All Spline types must implement:

```julia
point(curve,u)
```

and have field `controlpolygon`
