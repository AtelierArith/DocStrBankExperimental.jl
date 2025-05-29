```
Line(wl::F, log_gf::F, species::Species, E_lower::F,
     gamma_rad::Union{F, Missing}=missing, gamma_stark::Union{F, Missing}=missing,
     vdw::Union{F, Tuple{F, F}, Missing}, missing) where F <: Real
```

Arguments:

  * `wl`: wavelength (Assumed to be in cm if < 1, otherwise in Å)
  * `log_gf`: (log base 10) oscillator strength (unitless)
  * `species`: the `Species` associated with the line
  * `E_lower`: The energy (excitiation potential) of the lower energy level (eV)

Optional Arguments (these override default recipes):

  * `gamma_rad`: Fundemental width
  * `gamma_stark`: per-perturber Stark broadening width at 10,000 K (s⁻¹).
  * `vdW`: If this is present, it may may be

      * `log10(γ_vdW)`, assumed if negative
      * 0, corresponding to no vdW broadening
      * A fudge factor for the Unsoeld approximation, assumed if between 0 and 20
      * The [ABO parameters](https://github.com/barklem/public-data/tree/master/broadening-howto) as packed float (assumed if >= 20) or a `Tuple`, `(σ, α)`.

    This behavior is intended to mirror that of Turbospectrum as closely as possible.

See [`approximate_gammas`](@ref) for more information on the default recipes for `gamma_stark` and `vdW`.

Note the the "gamma" values here are FWHM, not HWHM, of the Lorenztian component of the line profile, and are in units of s⁻¹.

```
Line(line::line; kwargs...)
```

Construct a new `Line` by copying the values from an existing `Line`.  Any of the values can be modified with keyword arguments, e.g. `Line(line, log_gf=0.0)`.
