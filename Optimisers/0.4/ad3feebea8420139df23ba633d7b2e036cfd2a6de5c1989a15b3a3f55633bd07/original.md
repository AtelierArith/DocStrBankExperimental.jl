```
AdamW(η = 0.001, β = (0.9, 0.999), λ = 0, ϵ = 1e-8; couple = true)
AdamW(; [eta, beta, lambda, epsilon, couple])
```

[AdamW](https://arxiv.org/abs/1711.05101) is a variant of Adam fixing (as in repairing) its weight decay regularization. Implemented as an [`OptimiserChain`](@ref) of [`Adam`](@ref) and [`WeightDecay`](@ref)`.

# Parameters

  * Learning rate (`η == eta`): Amount by which gradients are discounted before updating                      the weights.
  * Decay of momentums (`β::Tuple == beta`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
  * Weight decay (`λ == lambda`): Controls the strength of $L_2$ regularisation.
  * Machine epsilon (`ϵ == epsilon`): Constant to prevent division by zero                        (no need to change default)
  * Keyword `couple`: If `true`, the weight decay is coupled with the learning rate, as in pytorch's AdamW.                   This corresponds to an update of the form `x = x - η * (dx + λ * x)`, where `dx` is the                   update from Adam with learning rate 1.                   If `false`, the weight decay is decoupled from the learning rate, in the spirit of the original paper.                   This corresponds to an update of the form `x = x - η * dx - λ * x`.                   Default is `true`.

!!! warning "Breaking change in v0.4"
    With version 0.4 the default update rule for AdamW has changed to match the pytorch implementation. The previous rule, which is closer to the original paper, can be obtained by setting `AdamW(..., couple=false)`. See [this issue](https://github.com/FluxML/Flux.jl/issues/2433) for more details.

