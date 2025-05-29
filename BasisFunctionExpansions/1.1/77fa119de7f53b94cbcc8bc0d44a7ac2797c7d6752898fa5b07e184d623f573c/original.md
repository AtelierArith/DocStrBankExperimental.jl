```
BasisFunctionApproximation(y::Vector, v, bfe::BasisFunctionExpansion, λ = 0)
```

Perform parameter identification to identify the Function `y = ϕ(v)`, where `ϕ` is a Basis Function Expansion of type `bfe`. `λ` is an optional regularization parameter (L² regularization).
