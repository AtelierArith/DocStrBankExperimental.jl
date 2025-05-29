```
LagrangianGradient{CO,T}
```

The gradient of the Lagrangian of a [`ConstrainedManifoldObjective`](@ref) `co` with respect to the variable $p$. The formula reads

$$
\operatorname{grad}_p \mathcal L(p; μ, λ)
= \operatorname{grad} f(p) +  \sum_{i=1}^m μ_i \operatorname{grad} g_i(p) + \sum_{j=1}^n λ_j \operatorname{grad} h_j(p)
$$

# Fields

  * `co::CO`, `μ::T`, `λ::T` as mentioned, where `T` represents a vector type.

# Constructor

```
LagrangianGradient(co, μ, λ)
```

Create a functor for the Lagrangian with fixed dual variables.

# Example

When you directly want to evaluate the gradient of the Lagrangian $\operatorname{grad}_p \mathcal L$ you can also call `LagrangianGradient(co, μ, λ)(M,p)` or `LagrangianGradient(co, μ, λ)(M,X,p)` for the in-place variant.
