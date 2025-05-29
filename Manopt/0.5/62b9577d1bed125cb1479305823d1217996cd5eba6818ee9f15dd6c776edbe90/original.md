```
LagrangianCost{CO,T} <: AbstractConstrainedFunctor{T}
```

Implement the Lagrangian of a [`ConstrainedManifoldObjective`](@ref) `co`.

$$
\mathcal L(p; μ, λ)
= f(p) +  \sum_{i=1}^m μ_ig_i(p) + \sum_{j=1}^n λ_jh_j(p)
$$

# Fields

  * `co::CO`, `μ::T`, `λ::T` as mentioned, where `T` represents a vector type.

# Constructor

```
LagrangianCost(co, μ, λ)
```

Create a functor for the Lagrangian with fixed dual variables.

# Example

When you directly want to evaluate the Lagrangian $\mathcal L$ you can also call

```
LagrangianCost(co, μ, λ)(M,p)
```
