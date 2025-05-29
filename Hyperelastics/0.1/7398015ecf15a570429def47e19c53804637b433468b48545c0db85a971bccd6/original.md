```julia
LambertDianiRey()
LambertDianiRey(type)

```

# Model:

$$
W = \int\limits_{3}^{I_1}\exp\bigg(\sum\limits_{i=0}^{n}a_i(I_1-3)^i\bigg)\text{d}I_1+\int\limits_{3}^{I_2}\sum\limits_{j=0}^{m}b_i\log(I_2)^i\text{d}I_2
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `a⃗`
  * `b⃗`

> Lambert-Diani J, Rey C. New phenomenological behavior laws for rubbers and thermoplastic elastomers. European Journal of Mechanics-A/Solids. 1999 Nov 1;18(6):1027-43.

