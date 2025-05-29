```
sigma2(pk, R)
```

Variance of mass fluctuation, σ^2, with a top-hat filter with radius `R`

# Arguments

  * `pk`(k): a function which returns a linear matter power spectrum with the argument k being the comoving wavenumber.

      * **pk times k^3 must be dimensionless**. For example, if k is in units of h/Mpc, `pk` must be in units of Mpc^3/h^3.
  * `R::Real`: a top-hat smoothing scale.

      * **R times k must be dimensionless**. For example, if k is in units of h/Mpc, `R` must be in units of Mpc/h.

`sigma2` is computed as

$σ^2(R) = ∫_0^∞ k^2dk W^2(kR) pk(k) / (2π^2)$

where and W(kR) is a window function given by

$W(x) = (3/x)j_1(x) = (3/x)(sin(x)/x^2 - cos(x)/x)$

j_1(x) is the spherical Bessel function of order 1.

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
