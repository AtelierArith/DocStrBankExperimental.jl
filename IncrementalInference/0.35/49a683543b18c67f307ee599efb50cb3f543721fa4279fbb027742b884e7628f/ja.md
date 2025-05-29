```julia
struct Circular <: DistributedFactorGraphs.InferenceVariable
```

Circularは、`theta in [-pi,pi)`の1回転の`Manifolds.Circle{ℝ}`のメカニズムです。
