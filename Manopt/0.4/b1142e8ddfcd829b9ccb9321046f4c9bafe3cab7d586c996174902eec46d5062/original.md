```
ExactPenaltyCost{S, Pr, R}
```

Represent the cost of the exact penalty method based on a [`ConstrainedManifoldObjective`](@ref) `P` and a parameter $ρ$ given by

$$
f(p) + ρ\Bigl(
    \sum_{i=0}^m \max\{0,g_i(p)\} + \sum_{j=0}^n \lvert h_j(p)\rvert
\Bigr),
$$

where an additional parameter $u$ is used as well as a smoothing technique, for example [`LogarithmicSumOfExponentials`](@ref) or [`LinearQuadraticHuber`](@ref) to obtain a smooth cost function. This struct is also a functor `(M,p) -> v` of the cost $v$.

## Fields

  * `ρ`, `u`: as described in the mathematical formula, .
  * `co`:     the original cost

## Constructor

```
ExactPenaltyCost(co::ConstrainedManifoldObjective, ρ, u; smoothing=LinearQuadraticHuber())
```
