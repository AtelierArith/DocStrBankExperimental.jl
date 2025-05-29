```julia
KhiemItskov()
KhiemItskov(type)

```

# Model:

$$
W = \mu_c \kappa n \log\bigg(\frac{\sin(\frac{\pi}{\sqrt{n}})(\frac{I_1}{3})^{\frac{q}{2}}}{\sin(\frac{\pi}{\sqrt{n}}(\frac{I_1}{3})^{\frac{q}{2}}}\bigg)+\mu_t\big[\frac{I_2}{3}^{1/2} - 1 \big]
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * μcκ
  * n
  * q
  * μt

> Khiêm VN, Itskov M. Analytical network-averaging of the tube model:: Rubber elasticity. Journal of the Mechanics and Physics of Solids. 2016 Oct 1;95:254-69.

