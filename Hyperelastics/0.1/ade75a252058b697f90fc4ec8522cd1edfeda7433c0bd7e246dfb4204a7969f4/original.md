```julia
Beatty()
Beatty(type)

```

# Model:

$$
W = -\frac{G_0 I_m(I_m-3)}{2(2I_m-3)}\log\bigg(\frac{1-\frac{I_1-3}{I_m-3}}{1+\frac{I_1-3}{I_m}} \bigg)
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `G₀`
  * `Iₘ`

> Beatty MF. On constitutive models for limited elastic, molecular based materials. Mathematics and mechanics of solids. 2008 Jul;13(5):375-87.

