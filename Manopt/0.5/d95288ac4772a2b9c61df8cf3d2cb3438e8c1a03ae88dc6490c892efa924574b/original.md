```
LagrangianHessian{CO, V, T}
```

The Hesian of the Lagrangian of a [`ConstrainedManifoldObjective`](@ref) `co` with respect to the variable $p$. The formula reads

$$
\operatorname{Hess}_p \mathcal L(p; μ, λ)[X]
= \operatorname{Hess} f(p) +  \sum_{i=1}^m μ_i \operatorname{Hess} g_i(p)[X] + \sum_{j=1}^n λ_j \operatorname{Hess} h_j(p)[X]
$$

# Fields

  * `co::CO`, `μ::T`, `λ::T` as mentioned, where `T` represents a vector type.

# Constructor

```
LagrangianHessian(co, μ, λ)
```

Create a functor for the Lagrangian with fixed dual variables.

# Example

When you directly want to evaluate the Hessian of the Lagrangian $\operatorname{Hess}_p \mathcal L$ you can also call `LagrangianHessian(co, μ, λ)(M, p, X)` or `LagrangianHessian(co, μ, λ)(M, Y, p, X)` for the in-place variant.
