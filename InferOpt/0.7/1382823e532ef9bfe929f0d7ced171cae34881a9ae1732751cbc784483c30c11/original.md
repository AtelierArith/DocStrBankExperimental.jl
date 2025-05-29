```
AbstractRegularized <: AbstractOptimizationLayer
```

Convex regularization perturbation of a black box linear (in θ) optimizer

```
ŷ(θ) = argmax_{y ∈ C} {θᵀg(y) + h(y) - Ω(y)}
```

with g and h functions of y.

# Interface

  * `(regularized::AbstractRegularized)(θ; kwargs...)`: return `ŷ(θ)`
  * `compute_regularization(regularized, y)`: return `Ω(y)
  * `get_maximizer(regularized)`: return the associated optimizer

# Available implementations

  * [`SoftArgmax`](@ref)
  * [`SparseArgmax`](@ref)
  * [`SoftRank`](@ref)
  * [`RegularizedFrankWolfe`](@ref)
