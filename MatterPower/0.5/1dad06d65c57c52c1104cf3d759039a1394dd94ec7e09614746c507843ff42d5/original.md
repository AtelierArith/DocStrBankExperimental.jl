```
dsigma2dR(pk, R)
```

Derivative of variance of mass fluctuation, dσ^2/dR,  with respect to a top-hat filter with radius `R`.

# Arguments

  * `pk`(k): a function which returns a linear matter power spectrum with the argument k being the comoving wavenumber.

      * **pk times k^3 must be dimensionless**. For example, if k is in units of h/Mpc, `pk` must be in units of Mpc^3/h^3.
  * `R::Real`: a top-hat smoothing scale.

      * **R times k must be dimensionless**. For example, if k is in units of h/Mpc, `R` must be in units of Mpc/h.

`dsigma2/dR` is computed as

$dσ^2/dR = 2 ∫_0^∞ k^2dk W(kR) dW/dR pk(k) / (2π^2)$

where and W(kR) is a window function given by

$W(x) = (3/x)j_1(x) = (3/x)(sin(x)/x^2 - cos(x)/x)$

and dW/dR is its derivative:

$dW/dR = k dW/dx = (-3k/x)j_2(x) = (-3k/x)[(3/x^2-1)sin(x)/x - 3cos(x)/x^2]$

j_n(x) is the spherical Bessel function of order n.

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
