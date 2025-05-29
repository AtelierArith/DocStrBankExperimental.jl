```julia
BechirChevalier(; ℒinv)

```

# Model:

$$
W = W_{3Chain}(\mu_f, N_3)+W_{8Chain}(\frac{\mu_c}{3}, N_8)
$$

where:

$$
\mu_f = \rho\sqrt{\frac{I_1}{3N_8}}
$$

$$
\mu_c = \bigg(1-\frac{\eta\alpha}{\sqrt{N_3}}\bigg)\mu_0
$$

$$
\alpha = \max{\lambda_1, \lambda_2, \lambda_3}
$$

# Arguments:

  * `ℒinv=TreloarApproximation()`: Sets the inverse Langevin approxamation used

# Parameters:

  * `μ₀`
  * `η`
  * `ρ`
  * `N₃`
  * `N₈`

> Bechir H, Chevalier L, Idjeri M. A three-dimensional network model for rubber elasticity: The effect of local entanglements constraints. International journal of engineering science. 2010 Mar 1;48(3):265-74.

