```julia
struct DynPoint2 <: DistributedFactorGraphs.InferenceVariable
```

速度成分を持つ2D空間の動的点: `x, y, dx/dt, dy/dt`
