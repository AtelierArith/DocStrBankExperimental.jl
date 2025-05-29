```julia
struct TVLogistic <: TransformVariables.ScalarTransform
```

Logistic transformation `x ↦ logit(x)`. Maps from all reals to (0, 1).
