```
halofit(pk, p, Ωmz, k)
```

This function returns a value of the non-linear power spectrum at a specified value of the comoving wavenumber.

*Reference*: Appendix of Takahashi et al., ApJ, 761, 152 (2012)

  * This reference updates parameters given in Appendix C of Smith et al., MNRAS, 341, 1311 (2003)
  * The terms proportional to (1+w) in Equation (A6, A7) of Takahashi et al. are not included in this function

# Arguments

  * `pk`(k): a function which returns a linear matter power spectrum with the argument k being the comoving wavenumber.
  * `p::Array{T,1} where T <: Real`: an array containing three variables [kσ, neff, C], which are obtained from `p = setup_halofit(pk)`.
  * `Ωmz::Real`: the matter density parameter at a given redshift z, e.g., $Ωmz = Ωm(1+z)^3 / [Ωm(1+z)^3 + Ωk(1+z)^2 + ΩΛ]$.
  * `k::Real`: comoving wavenumber.

      * **pk times k^3 must be dimensionless**. For example, if `k` is in units of h/Mpc, `pk` must be in units of Mpc^3/h^3.

This function is based on [Cosmology Routine Library (CRL)](https://wwwmpa.mpa-garching.mpg.de/~komatsu/crl/).
