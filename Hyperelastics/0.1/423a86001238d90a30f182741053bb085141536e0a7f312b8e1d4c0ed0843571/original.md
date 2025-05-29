```julia
NonaffineMicroSphere(; ℒinv, n)

```

# Model: See Paper

# Arguments:

  * `ℒinv=CohenRounded3_2()`: Sets the inverse Langevin approximation used.
  * `n=21`: Order of quadrature for spherical integration

# Parameters:

  * μ: Small strain shear modulus
  * N: Number of chain segments
  * p: Non-affine stretch parameter
  * U: Tube geometry parameter
  * q: Non-affine tube parameter

> Miehe C, Göktepe S, Lulei F. A micro-macro approach to rubber-like materials—part I: the non-affine micro-sphere model of rubber elasticity. Journal of the Mechanics and Physics of Solids. 2004 Nov 1;52(11):2617-60.

