```julia
Biderman()
Biderman(type)

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
  * `C20`
  * `C30`

> Biderman VL. Calculation of rubber parts. Rascheti na prochnost. 1958;40.

