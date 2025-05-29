```julia
EdwardVilgis()

```

# Model:

$$
W = \frac{1}{2}N_C\Bigg[\frac{(1-\alpha^2)I_1}{1-\alpha^2I_1}+\log(1-\alpha^2I_1)\Bigg]+\frac{1}{2}N_S\Bigg[\sum_{i=1}^{3}\Big\{\frac{(1+\eta)(1-\alpha^2)\lambda_i^2}{( 1+\eta\lambda_i^2)(1-\alpha^2I_1)}+\log(1+\eta\lambda_i^2)\Big\}+\log(1-\alpha^2I_1)\Bigg]
$$

# Parameters:

  * `Ns`: Number of sliplinks
  * `Nc`: Number of crosslinks
  * `α`: A measure of chain inextensibility
  * `η`: A measure of the amount of chain slippage

# Note:

  * Since α and η result from the same mechanism, they should be of approximately the same order of magnitude. Large differences between the two may indicate an issue with the optimizer or initial guess.

> Edwards SF, Vilgis T. The effect of entanglements in rubber elasticity. Polymer. 1986 Apr 1;27(4):483-92.

