```
d2sigma2gausdR2(pk, R)
```

Second derivative of variance of mass fluctuation, d^2σ^2/dR^2, with respect to a Gaussian filter with width `R`.

# Arguments

  * `pk`(k): a function which returns a linear matter power spectrum with the argument k being the comoving wavenumber.

      * **pk times k^3 must be dimensionless**. For example, if k is in units of h/Mpc, `pk` must be in units of Mpc^3/h^3.
  * `R::Real`: a top-hat smoothing scale.

      * **R times k must be dimensionless**. For example, if k is in units of h/Mpc, `R` must be in units of Mpc/h.

`d2sigma2gaus/dR2` is computed as

$d^2σ^2/dR^2 = -2 ∫_0^∞ (1 - 2x^2) k^4dk exp(-k^2 R^2) pk(k) / (2π^2)$

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
