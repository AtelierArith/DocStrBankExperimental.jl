```
WeightDecay(γ = 5f-4)
```

Decay weights by $γ$, that is, add `γ .* x` to the gradient `x̄` which will be subtracted from `x`.

Typically composed  with other optimisers as the first transformation in an [`OptimiserChain`](@ref). This is equivalent to adding $L_2$ regularization with coefficient $γ$ to the loss.

# Parameters

  * Weight decay (`γ`): Decay applied to weights during optimisation.
