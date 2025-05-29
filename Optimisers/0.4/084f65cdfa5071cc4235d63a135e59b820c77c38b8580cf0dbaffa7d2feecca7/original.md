```
WeightDecay(λ = 5e-4)
WeightDecay(; [lambda])
```

Implements $L_2$ regularisation, also known as ridge regression,  when composed  with other rules as the first transformation in an [`OptimiserChain`](@ref).

It does this by adding `λ .* x` to the gradient. This is equivalent to adding  `λ/2 * sum(abs2, x) == λ/2 * norm(x)^2` to the loss.

See also [`SignDecay`] for $L_1$ normalisation.

# Parameters

  * Penalty (`λ ≥ 0`): Controls the strength of the regularisation.
