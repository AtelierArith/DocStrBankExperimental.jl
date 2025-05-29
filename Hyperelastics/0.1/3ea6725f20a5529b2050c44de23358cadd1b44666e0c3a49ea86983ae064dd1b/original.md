```julia
ABGI(; ℒinv)

```

# Model:

$$
W = W_{Arruda-Boyce} + \frac{G_e}{n} \left(\sum_{i=1}^{3}\lambda_i^n-3\right)
$$

# Arguments:

  * `ℒinv = TreloarApproximation()`: Sets the inverse Langevin approxamationused (default = `TreloarApproximation()`)

# Parameters:

  * `μ`
  * `N`
  * `Ge`
  * `n`

> Meissner B, Matějka L. A Langevin-elasticity-theory-based constitutiveequation for rubberlike networks and its comparison with biaxialstress–strain data. Part I. Polymer. 2003 Jul 1;44(16):4599-610.

