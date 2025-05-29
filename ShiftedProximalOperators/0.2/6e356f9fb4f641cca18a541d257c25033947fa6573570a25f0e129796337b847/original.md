```
prox!(y, ψ, q, σ)
```

Evaluate the proximal operator of a shifted regularizer, i.e, return a solution s of

```
minimize{s}  ½ σ⁻¹ ‖s - q‖₂² + ψ(s),
```

where

  * ψ is a `ShiftedProximableFunction` representing a model of h(x + s) and possibly including the indicator of a trust region;
  * q is the vector where the shifted proximal operator should be evaluated;
  * σ is a positive regularization parameter.

The solution is stored in the input vector `y` an `y` is returned.
