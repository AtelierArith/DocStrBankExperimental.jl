```
iprox!(y, ψ, g, d)
```

Evaluate the indefinite proximal operator of a separable box shifted regularizer, i.e, return a solution y of

```
minimize{y}  ½ yᵀDy + gᵀy + ψ(y)
```

where

  * ψ is a `ShiftedProximableFunction` representing a model of the sum of a separable function h(x + s) and the indicator of a trust region;
  * g is a vector;
  * `D = Diagonal(d)` where d is a vector.

The solution is stored in the input vector `y` an `y` is returned.
