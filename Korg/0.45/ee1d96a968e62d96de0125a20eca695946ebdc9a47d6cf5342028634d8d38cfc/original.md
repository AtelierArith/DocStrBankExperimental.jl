```
synth(kwargs...)
```

This function creates a synthetic spectrum. It's easier to use than [`synthesize`](@ref), but it gives you less control. Unlike [`synthesize`](@ref), it **returns a tuple of `(wavelengths, rectified_flux, cntm)`** (Wavelength in Å, rectified flux as a unitless number between 0 and 1, and continuum in erg/s/cm^5).  `Korg.synth` also provides shortcuts for some ways you might want to post-process the spectrum (applying a LSF, rotation, etc).

# Keyword arguments

  * `Teff`: effective temperature in K (default: 5000)
  * `logg`: surface gravity in cgs units (default: 4.5)
  * `m_H`: metallicity, [metals/H], (default: 0.0) (See [`format_A_X`](@ref) for precisely how this is interpreted.)
  * `alpha_H`: alpha enhancement, [α/H], (default: `m_H`) (See [`format_A_X`](@ref) for precisely how this is interpreted.)
  * *Any atomic symbol* (e.g. `Fe` or `C`) can be used to to specify a (solar relative, [*X*/H]) abundance. These override `m_H` and `alpha_H`. Specifying an individual abundance means that the true metallicity and alpha will not correspond precisely to the values of `m_H` and `alpha_H`. See [`format_A_X`](@ref) for details.
  * `linelist`: a linelist, (default: [`get_VALD_solar_linelist()`](@ref)). See also [`read_linelist`](@ref).
  * `wavelengths`: a tuple of the start and end wavelengths (default: (5000, 6000)), or a vector of `(λstart, λstop)` pairs. See [`Wavelengths`](@ref) for all the ways the wavelengths can be specified.
  * `rectify`: whether to rectify (continuum normalize) the spectrum (default: true)
  * `R`: resolution (default: `Inf`, no LSF applied). `R` can be a scalar, or a function from wavelength (in Å) to resolving power. See [`apply_LSF`](@ref) for details on how to do this manually.
  * `vsini`: projected rotational velocity in km/s (default: 0). See [`apply_rotation`](@ref) for details on how to do this manually.
  * `vmic`: microturbulent velocity in km/s (default: 1.0).
  * `synthesize_kwargs`: additional keyword arguments pass to [`synthesize`](@ref).
  * `format_A_X_kwargs`: additional keyword arguments pass to [`format_A_X`](@ref).
