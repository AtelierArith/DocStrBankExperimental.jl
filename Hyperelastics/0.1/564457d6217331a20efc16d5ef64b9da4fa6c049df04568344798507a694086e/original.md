```julia
DavisDeThomas()
DavisDeThomas(type)

```

# Model:

$$
W = \frac{A}{2(1-\frac{n}{2})}(I_1-3+C^2)^{1-\frac{n}{2}}+k(I_1-3)^2
$$

# Arguments

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `A`
  * `n`
  * `C`
  * `k`

> Davies CK, De DK, Thomas AG. Characterization of the behavior of rubber for engineering design purposes. 1. Stress-strain relations. Rubber chemistry and technology. 1994 Sep;67(4):716-28.

