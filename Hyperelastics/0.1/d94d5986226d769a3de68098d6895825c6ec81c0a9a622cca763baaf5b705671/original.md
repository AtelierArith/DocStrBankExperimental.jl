```julia
PucciSaccomandi()
PucciSaccomandi(type)

```

# Model:

$$
W = K\log{\frac{I_2}{3}}-\frac{\mu J_m}{2}\log{1-\frac{I_1-3}{J-m}}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `K`
  * `μ`
  * `Jₘ`

> Pucci E, Saccomandi G. A note on the Gent model for rubber-like materials. Rubber chemistry and technology. 2002 Nov;75(5):839-52.

