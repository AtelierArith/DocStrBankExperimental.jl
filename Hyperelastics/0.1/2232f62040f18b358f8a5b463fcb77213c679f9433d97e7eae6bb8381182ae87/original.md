```julia
ArrudaBoyce(; ...)
ArrudaBoyce(type; ℒinv)

```

# Model:

$$
W = \mu N \left( \frac{\lambda_{chain}}{\sqrt{N}} \beta + \log\left(\frac{\beta}{\sinh\beta}\right) \right)
$$

where

$$
\beta = \mathcal{L}^{-1}\left(\frac{\lambda_{chain}}{\sqrt{N}}\right)
$$

and

$$
\lambda_{chain} = \sqrt{\frac{I_1}{3}}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()`
  * `ℒinv=TreloarApproximation()`: Sets the inverse Langevin approxamation used

# Parameters:

  * `μ`: Small strain shear modulus
  * `N`: Square of the locking stretch of the network.

> Arruda EM, Boyce MC. A three-dimensional constitutive model for the large stretch behavior of rubber elastic materials. Journal of the Mechanics and Physics of Solids. 1993 Feb 1;41(2):389-412.

