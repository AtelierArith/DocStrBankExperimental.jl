```julia
struct Circular <: DistributedFactorGraphs.InferenceVariable
```

Circular is a `Manifolds.Circle{ℝ}` mechanization of one rotation, with `theta in [-pi,pi)`.
