```julia
Amin()
Amin(type)

```

# Model:

$$
W = C_1 (I_1 - 3) + \frac{C_2}{N + 1} (I_1 - 3)^{N + 1} + \frac{C_3}{M + 1} (I_1 - 3)^{M + 1} + C_4 (I_2 - 3)
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `C1`
  * `C2`
  * `C3`
  * `C4`
  * `N`
  * `M`

> Amin AF, Wiraguna SI, Bhuiyan AR, Okui Y. Hyperelasticity model for finite element analysis of natural and high damping rubbers in compression and shear. Journal of engineering mechanics. 2006 Jan;132(1):54-64.

