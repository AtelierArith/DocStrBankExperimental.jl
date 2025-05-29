```julia
HartmannNeff()
HartmannNeff(type)

```

# Model:

$$
W = \sum\limits_{i,j=0}^{M,N}C_{i,0}(I_1-3)^i -3\sqrt{3}^j+\alpha(I_1-3)
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()`

# Parameters:

  * `α`
  * `Ci⃗0`
  * `C0j⃗`

> Hartmann S, Neff P. Polyconvexity of generalized polynomial-type hyperelastic strain energy functions for near-incompressibility. International journal of solids and structures. 2003 Jun 1;40(11):2767-91.

