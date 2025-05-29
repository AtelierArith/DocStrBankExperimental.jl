```julia
LopezPamies()
LopezPamies(type)

```

# Model:

$$
W = \frac{3^{1 - \alpha_i}}{2\alpha_i} \mu_i (I_1^{\alpha_i} - 3^{\alpha_i})
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `α⃗`
  * `μ⃗`

> Lopez-Pamies O. A new I1-based hyperelastic model for rubber elastic materials. Comptes Rendus Mecanique. 2010 Jan 1;338(1):3-11.

