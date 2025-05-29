```
@enum BiasFunction
```

Specifies a bias function when choosing parents to mating. This function substitutes the $\rho$ (rho) parameter from the original BRKGA. For a given rank $r$, we have the following functions:

  * `CONSTANT`: 1 / number of parents for mating (all individuals have the             same probability)
  * `CUBIC`: $r^{-3}$
  * `EXPONENTIAL`: $ϵ^{-r}$
  * `LINEAR`: $1 / r$
  * `LOGINVERSE`: $1 / \log(r + 1)$
  * `QUADRATIC`: $r^{-2}$
