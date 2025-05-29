```
EvaluateEach(geos::AbstractVector{<:AbstractODESolution}, Ts::AbstractVector) -> Vector
```

Evalues a family `geos` of geodesics on a set of parameters `Ts`. `geos[1]` is evaluated at `Ts[1]`, `geos[2]` is evaluated at `Ts[2]` and so on. The second half of the values respresenting the velocities is automatically truncated.
