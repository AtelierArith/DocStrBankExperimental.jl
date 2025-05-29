```julia
ThreeChainModel(; ℒinv)

```

# Model:

$$
W = \frac{\mu\sqrt{N}}{3}\sum\limits_{i=1}^{3}\bigg(\lambda_i\beta_i+\sqrt{N}\log\bigg(\frac{\beta_i}{\sinh \beta_i}\bigg)\bigg)
$$

# Arguments:

  * `ℒinv=TreloarApproximation()`: Sets the inverse Langevin approxamation used

# Parameters:

  * `μ`: Small strain shear modulus
  * `N`: Square of the locking stretch of the network.

> James HM, Guth E. Theory of the elastic properties of rubber. The Journal of Chemical Physics. 1943 Oct;11(10):455-81.

