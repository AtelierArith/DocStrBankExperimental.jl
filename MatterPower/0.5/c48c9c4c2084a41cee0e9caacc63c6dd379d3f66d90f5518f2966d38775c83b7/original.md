```
setup_halofit(pk)
```

This function returns three parameters, [kσ, neff, C],  which are needed for computation of the halofit non-linear power spectrum.

*Reference*: Appendix C of Smith et al., MNRAS, 341, 1311 (2003)

# Arguments

  * `pk`(k): a function which returns a linear matter power spectrum with the argument k being the comoving wavenumber.

      * **pk times k^3 must be dimensionless**. For example, if k is in units of h/Mpc, `pk` must be in units of Mpc^3/h^3.

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
