```julia
GornetDesmorat()
GornetDesmorat(type)

```

# Model:

$$
W = h_1\int\exp{h_3(I_1-3)^2}\text{d}I_1+3h_2\int\frac{1}{\sqrt{I_2}}\text{d}I_2 = \frac{h_1 \sqrt{\pi} \text{erfi}(\sqrt{h_3}(I_1-3)^2)}{2\sqrt{h_3}}+6h_2\sqrt{I_2}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * h₁
  * h₂
  * h₃

# Notes:

  * The differential form was original form and the closed form SEF was determine via symbolic integration in Mathematica. The model is not compatible with AD and has methods for the Second Piola Kirchoff Stress Tensor and Cauchy Stress Tensor implemented.

> Gornet L, Marckmann G, Desmorat R, Charrier P. A new isotropic hyperelastic strain energy function in terms of invariants and its derivation into a pseudo-elastic model for Mullins effect: application to finite element analysis. Constitutive Models for Rubbers VII. 2012:265-71.

