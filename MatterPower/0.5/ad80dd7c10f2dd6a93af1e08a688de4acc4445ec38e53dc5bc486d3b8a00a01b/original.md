```
dsigma2gausdR(pk, R)
```

Derivative of variance of mass fluctuation, dσ^2/dR, with respect to a Gaussian filter with width `R`.

# Arguments

  * `pk`(k): a function which returns a linear matter power spectrum with the argument k being the comoving wavenumber.

      * **pk times k^3 must be dimensionless**. For example, if k is in units of h/Mpc, `pk` must be in units of Mpc^3/h^3.
  * `R::Real`: a top-hat smoothing scale.

      * **R times k must be dimensionless**. For example, if k is in units of h/Mpc, `R` must be in units of Mpc/h.

`dsigma2gaus/dR` is computed as

$dσ^2/dR = -2R ∫_0^∞ k^4dk exp(-k^2 R^2) pk(k) / (2π^2)$

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
