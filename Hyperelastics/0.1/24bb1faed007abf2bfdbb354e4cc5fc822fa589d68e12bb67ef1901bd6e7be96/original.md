```julia
JamesGreenSimpson()
JamesGreenSimpson(type)

```

# Model:

$$
W = \sum\limits_{i,j=0}^{3, 1}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()`

# Parameters:

  * `C10`
  * `C01`
  * `C11`
  * `C20`
  * `C30`

> James AG, Green A, Simpson GM. Strain energy functions of rubber. I. Characterization of gum vulcanizates. Journal of Applied Polymer Science. 1975 Jul;19(7):2033-58.

