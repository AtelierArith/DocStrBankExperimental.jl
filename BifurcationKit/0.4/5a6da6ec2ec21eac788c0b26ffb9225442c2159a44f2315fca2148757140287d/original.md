```
pb = DeflatedProblem(prob, M::DeflationOperator, jactype)
```

Create a `DeflatedProblem`.

This creates a deflated functional (problem) $M(u) \cdot F(u) = 0$ where `M` is a `DeflationOperator` which encodes the penalization term. `prob` is an `AbstractBifurcationProblem` which encodes the functional. It is not meant not be used directly albeit by advanced users.

## Arguments

  * `jactype` select the jacobian for the newton solve. Can be `Val(:autodiff)`, `Val(:fullIterative)`, `Val(:Custom)`
