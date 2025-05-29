```julia
HossMarczakI()
HossMarczakI(type)

```

# Model:

$$
W = \frac{\alpha}{\beta}(1-\exp{-\beta(I_1-3)})+\frac{\mu}{2b}\bigg((1+\frac{b}{n}(I_1-3))^n -1\bigg)
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `α`
  * `β`
  * `μ`
  * `b`
  * `n`

# Note:

  * The authors suggested this model for low strains.

> Hoss L, Marczak RJ. A new constitutive model for rubber-like materials. Mecánica Computacional. 2010;29(28):2759-73.

