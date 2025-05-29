```
t_nowiggle(k, ωm, fbaryon)
```

Transfer function for the linear matter power spectrum without Baryon Acoustic Oscillation (the so-called *no-wiggle* transfer function).

*Reference*: Equation (29-31) of Eisenstein and Hu, ApJ, 496, 605 (1998)

# Arguments

  * `k::Real`: the comoving wavenumber **in units of 1/Mpc**. I.e., there is **no h** in the wavenumber.
  * `ωm::Real`: the physical baryon density parameter, `ωm` = Ωm h^2
  * `fbaryon::Real`: the baryon fraction,  `fbaryon` = Ωb/Ωb

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
