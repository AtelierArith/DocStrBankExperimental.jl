```julia
HainesWilson()
HainesWilson(type)

```

# Model:

$$
W = \sum\limits_{i,j=0}^{3, 2}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()`

# Parameters:

  * `C10`
  * `C01`
  * `C11`
  * `C02`
  * `C20`
  * `C30`

> Haines DW, Wilson WD. Strain-energy density function for rubberlike materials. Journal of the Mechanics and Physics of Solids. 1979 Aug 1;27(4):345-60.

