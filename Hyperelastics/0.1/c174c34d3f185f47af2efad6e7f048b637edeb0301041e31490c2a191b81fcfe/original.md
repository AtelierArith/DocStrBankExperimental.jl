```julia
HartSmith()
HartSmith(type)

```

# Model:

$$
W = \frac{G\exp{(-9k_1+k_1I_1)}}{k_1}+Gk_2\log{I_2}
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()

# Parameters:

  * `G`
  * `k₁`
  * `k₂`

> Hart-Smith LJ. Elasticity parameters for finite deformations of rubber-like materials. Zeitschrift für angewandte Mathematik und Physik ZAMP. 1966 Sep;17(5):608-26.

