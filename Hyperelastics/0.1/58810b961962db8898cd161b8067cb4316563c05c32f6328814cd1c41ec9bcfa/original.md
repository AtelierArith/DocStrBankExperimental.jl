```julia
GenYeoh()
GenYeoh(type)

```

# Model:

$$
W = K_1 (I_1 - 3)^m + K_2 * (I_1 - 3)^p + K_3 * (I_1 - 3)^q
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `K1`
  * `K2`
  * `K3`
  * `m`
  * `p`
  * `q`

> Hohenberger TW, Windslow RJ, Pugno NM, Busfield JJ. A constitutive model for both low and high strain nonlinearities in highly filled elastomers and implementation with user-defined material subroutines in ABAQUS. Rubber Chemistry and Technology. 2019;92(4):653-86.

