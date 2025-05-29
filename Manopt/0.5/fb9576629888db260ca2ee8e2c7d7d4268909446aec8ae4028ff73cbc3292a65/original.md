```
AugmentedLagrangianGrad{CO,R,T} <: AbstractConstrainedFunctor{T}
```

Stores the parameters $ρ ∈ ℝ$, $μ ∈ ℝ^m$, $λ ∈ ℝ^n$ of the augmented Lagrangian associated to the [`ConstrainedManifoldObjective`](@ref) `co`.

This struct is also a functor in both formats

  * `(M, p) -> X` to compute the gradient in allocating fashion.
  * `(M, X, p)` to compute the gradient in in-place fashion.

additionally this gradient does accept a positional last argument to specify the `range` for the internal gradient call of the constrained objective.

based on the internal [`ConstrainedManifoldObjective`](@ref) and computes the gradient `$(_tex(:grad))$(_tex(:Cal, "L"))_{ρ}(p, μ, λ)``, see also [`AugmentedLagrangianCost`](@ref).

## Fields

  * `co::CO`, `ρ::R`, `μ::T`, `λ::T` as mentioned in the formula, where $R$ should be the

number type used and $T$ the vector type.

# Constructor

```
AugmentedLagrangianGrad(co, ρ, μ, λ)
```
