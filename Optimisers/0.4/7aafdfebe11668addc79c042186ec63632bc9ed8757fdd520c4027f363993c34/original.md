```
SignDecay(λ = 1e-3)
SignDecay(; [lambda])
```

Implements $L_1$ regularisation, also known as LASSO regression, when composed  with other rules as the first transformation in an [`OptimiserChain`](@ref).

It does this by adding `λ .* sign(x)` to the gradient. This is equivalent to adding  `λ * sum(abs, x) == λ * norm(x, 1)` to the loss.

See also [`WeightDecay`] for $L_2$ normalisation. They can be used together: `OptimiserChain(SignDecay(0.012), WeightDecay(0.034), Adam())` is equivalent to adding `0.012 * norm(x, 1) + 0.017 * norm(x, 2)^2` to the loss function.

# Parameters

  * Penalty (`λ ≥ 0`): Controls the strength of the regularisation.
