```julia
AnsarriBenam(; ...)
AnsarriBenam(type; n)

```

# Model:

$$
W = \frac{3(n-1)}{2n}\mu N \left[\frac{1}{3N(n-1)}(I_1 - 3) - \log{\frac{I_1 - 3N}{3 -3N}} \right]
$$

# Arguments:

  * `type=PrincipalValueForm()`: Sets the form of the strain energy density function. Either `PrincipalValueForm()` or `InvariantForm()
  * `ℒinv=TreloarApproximation()`: Sets the inverse Langevin approxamation used (default = ``)
  * `n::Int=3`: Sets the order of the model

# Parameters:

  * `μ`
  * `n`
  * `N`

> Anssari-Benam A. On a new class of non-Gaussian molecular-based constitutive models with limiting chain extensibility for incompressible rubber-like materials. Mathematics and Mechanics of Solids. 2021 Nov;26(11):1660-74.

