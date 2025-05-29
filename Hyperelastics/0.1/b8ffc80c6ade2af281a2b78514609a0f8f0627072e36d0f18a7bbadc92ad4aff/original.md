```julia
Swanson()
Swanson(type)

```

# Model:

$$
W = \sum\limits_{i=1}^{N} \frac{3}{2}(\frac{A_i}{1+\alpha_i}(\frac{I_1}{3})^{1+\alpha_i}+\frac{B_i}{1+\beta_i}(\frac{I_2}{3})^{1+\beta_i}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `A⃗`
  * `α⃗`
  * `B⃗`
  * `β⃗`

> Swanson SR. A constitutive model for high elongation elastic materials.

