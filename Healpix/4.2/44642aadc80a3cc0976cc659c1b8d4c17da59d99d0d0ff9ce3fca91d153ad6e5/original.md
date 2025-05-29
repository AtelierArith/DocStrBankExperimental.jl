An array of harmonic coefficients (a_ℓm).

The type `T` is used for the value of each harmonic coefficient, and it must be a `Number` (one should however only use complex types for this). The type `AA` is used to store the array of coefficients; a typical choice is `Vector`.

A `Alm` type contains the following fields:

  * `alm`: the array of harmonic coefficients
  * `lmax`: the maximum value for $ℓ$
  * `mmax`: the maximum value for $m$
  * `tval`: maximum number of $m$ coefficients for the maximum $ℓ$

The $a_{\ell m}$ are stored by $m$: if $\ell_{max}$ is 16, the first 16 elements are $m=0$, $\ell=0-16$, then the following 15 elements are $m=1$, $\ell=1-16$, then $m=2$, $\ell=2-16$ and so on until the last element, the 153th, is $m=16$, $\ell=16$.
