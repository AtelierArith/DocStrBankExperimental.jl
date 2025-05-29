```julia
struct FenchelYoungLoss{O<:InferOpt.AbstractOptimizationLayer} <: InferOpt.AbstractLossLayer
```

Fenchel-Young loss associated with a given optimization layer.

```
L(θ, y_true) = (Ω(y_true) - θᵀy_true) - (Ω(ŷ) - θᵀŷ)
```

Reference: [https://arxiv.org/abs/1901.02324](https://arxiv.org/abs/1901.02324)

# Fields

  * `optimization_layer::AbstractOptimizationLayer`: optimization layer that can be formulated as `ŷ(θ) = argmax {θᵀy - Ω(y)}` (either regularized or perturbed)

# Compatibility

This loss is compatible with:

  * [`LinearMaximizer`](@ref)-based layers.
  * [`PerturbedOracle`](@ref) layers, with additive or multiplicative perturbations (generic perturbations are not supported).
  * any [`AbstractRegularized`](@ref) layer.
