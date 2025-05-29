```
AugmentedLagrangianCost{CO,R,T} <: AbstractConstrainedFunctor
```

Stores the parameters $ρ ∈ ℝ$, $μ ∈ ℝ^m$, $λ ∈ ℝ^n$ of the augmented Lagrangian associated to the [`ConstrainedManifoldObjective`](@ref) `co`.

This struct is also a functor `(M,p) -> v` that can be used as a cost function within a solver, based on the internal [`ConstrainedManifoldObjective`](@ref) it computes

$$
\mathcal L_\rho(p, μ, λ)
= f(x) + \frac{ρ}{2} \biggl(
    \sum_{j=1}^n \Bigl( h_j(p) + \frac{λ_j}{ρ} \Bigr)^2
    +
    \sum_{i=1}^m \max\Bigl\{ 0, \frac{μ_i}{ρ} + g_i(p) \Bigr\}^2
\Bigr)
$$

## Fields

  * `co::CO`, `ρ::R`, `μ::T`, `λ::T` as mentioned in the formula, where $R$ should be the

number type used and $T$ the vector type.

# Constructor

```
AugmentedLagrangianCost(co, ρ, μ, λ)
```
