```
FunctionVectorialType{P<:AbstractPowerRepresentation} <: AbstractVectorialType
```

A type to indicate that constraints are implemented one whole functions, for example $g(p) ∈ ℝ^m$ or $\operatorname{grad} g(p) ∈ (T_p\mathcal M)^m$.

This type internally stores the [`AbstractPowerRepresentation`](@extref `ManifoldsBase.AbstractPowerRepresentation`), when it makes sense, especially for Hessian and gradient functions.
