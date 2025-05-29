```julia
Lim(; ...)
Lim(type; ℒinv)

```

# Model:

$$
W = \left(1-f\left(\frac{I_1-3}{\hat{I_1}-3}\right)\right)W_{NeoHookean}(μ₁)+fW_{ArrudaBoyce}(μ₂, N)
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()
  * `ℒinv=TreloarApproximation()`: Sets the inverse Langevin approxamation used

# Parameters:

  * `μ₁`
  * `μ₂`
  * `N`
  * `Î₁`

> Lim GT. Scratch behavior of polymers. Texas A&M University; 2005.

