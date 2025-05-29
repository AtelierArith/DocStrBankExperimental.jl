```julia
struct SPOPlusLoss{F} <: InferOpt.AbstractLossLayer
```

Convex surrogate of the Smart "Predict-then-Optimize" loss.

# Fields

  * `maximizer::Any`: linear maximizer function of the form `θ -> ŷ(θ) = argmax θᵀy`
  * `α::Float64`: convexification parameter, default = 2.0

Reference: [https://arxiv.org/abs/1710.08005](https://arxiv.org/abs/1710.08005)
