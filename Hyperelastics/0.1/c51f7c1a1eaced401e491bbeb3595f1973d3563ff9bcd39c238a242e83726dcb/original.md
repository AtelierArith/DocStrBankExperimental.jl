```julia
Gent()
Gent(type)

```

# Model:

$$
W = -\frac{\mu J_m}{2}\log{\bigg(1-\frac{I_1-3}{J_m}\bigg)}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `μ`:  Small strain shear modulus
  * `Jₘ`: Limiting stretch invariant

> Gent AN. A new constitutive relation for rubber. Rubber chemistry and technology. 1996 Mar;69(1):59-61.

