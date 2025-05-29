```
ExactPenaltyGrad{S, CO, R}
```

Represent the gradient of the [`ExactPenaltyCost`](@ref) based on a [`ConstrainedManifoldObjective`](@ref) `co` and a parameter $ρ$ and a smoothing technique, which uses an additional parameter $u$.

This struct is also a functor in both formats

  * `(M, p) -> X` to compute the gradient in allocating fashion.
  * `(M, X, p)` to compute the gradient in in-place fashion.

## Fields

  * `ρ`, `u` as stated before
  * `co` the nonsmooth objective

## Constructor

```
ExactPenaltyGradient(co::ConstrainedManifoldObjective, ρ, u; smoothing=LinearQuadraticHuber())
```
