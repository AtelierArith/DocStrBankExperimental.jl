```
synthesize(atm, linelist, A_X, (λ_start, λ_stop); kwargs... )
synthesize(atm, linelist, A_X, wavelength_ranges; kwargs... )
```

Compute a synthetic spectrum. Returns a [`SynthesisResult`](@ref).

# Arguments

  * `atm`: the model atmosphere (see [`read_model_atmosphere`](@ref))
  * `linelist`: A vector of [`Line`](@ref)s (see [`read_linelist`](@ref), [`get_APOGEE_DR17_linelist`](@ref), and [`get_VALD_solar_linelist`](@ref)).
  * `A_X`: a vector containing the A(X) abundances (log(X/H) + 12) for elements from hydrogen to uranium.  (see [`format_A_X`](@ref))
  * The wavelengths at which to synthesize the spectrum.  They can be specified either as a pair `(λstart, λstop)`, or as a list of pairs `[(λstart1, λstop1), (λstart2, λstop2), ...]`.
  * `λ_start`: the lower bound (in Å) of the region you wish to synthesize.
  * `λ_stop`: the upper bound (in Å) of the region you wish to synthesize.
  * `λ_step` (default: 0.01): the (approximate) step size to take (in Å).

# Example

To synthesize a spectrum between 5000 Å and 5100 Å, with all metal abundances set to 0.5 dex less than the solar value except carbon, which we set to [C/H]=-0.25:

```
atm = read_model_atmosphere("path/to/atmosphere.mod")
linelist = read_linelist("path/to/linelist.vald")
A_X = format_A_X(-0.5, Dict("C" => -0.25))
result = synthesize(atm, linelist, A_X, 5000, 5100)
```

# Optional arguments:

  * `vmic` (default: 0) is the microturbulent velocity, $\xi$, in km/s.
  * `line_buffer` (default: 10): the farthest (in Å) any line can be from the provided wavelength range before it is discarded.  If the edge of your window is near a strong line, you may have to turn this up.
  * `cntm_step` (default 1): the distance (in Å) between point at which the continuum opacity is calculated.
  * `hydrogen_lines` (default: `true`): whether or not to include H lines in the synthesis.
  * `use_MHD_for_hydrogen_lines` (default: `true`): whether or not to use the MHD occupation probability formalism for hydrogen lines. (MHD is always used for hydrogen bound-free absorption.)
  * `hydrogen_line_window_size` (default: 150): the maximum distance (in Å) from each hydrogen line center at which to calculate its contribution to the total absorption coefficient.
  * `mu_values` (default: 20): the number of μ values at which to calculate the surface flux, or a vector of the specific values to use when doing transfer in spherical geometry. If `mu_points` is an integer, the values are chosen per Gauss-Legendre integration. If they are specified directly, the trapezoid rule is used for the astrophysical flux. The default values is sufficient for accuracy at the 10^-3 level. Note that if you are using the default radiative transfer scheme, with a plane-parallel model atmosphere, the integral over μ is exact, so this parameter has no effect. The points and weights are returned in the `mu_grid` field of the output.
  * `line_cutoff_threshold` (default: `3e-4`): the fraction of the continuum absorption coefficient at which line profiles are truncated.  This has major performance impacts, since line absorption calculations dominate more syntheses.  Turn it down for more precision at the expense of runtime. The default value should effect final spectra below the 10^-3 level.
  * `electron_number_density_warn_threshold` (default: `Inf`): if the relative difference between the calculated electron number density and the input electron number density is greater than this value, a warning is printed.  By default, this warning is suppress (threshold is `Inf`) because it is very easily raised in cases where it is of no observable consequence. See also `electron_number_density_warn_min_value`, below.
  * `electron_number_density_warn_min_value` (default: `1e-4`): The minimum value of the ratio of the electron number density to the total number density at which a warning is printed.
  * `return_cntm` (default: `true`): whether or not to return the continuum at each wavelength.  If this is false, `solution.cntm` will be `nothing`.
  * `ionization_energies`, a `Dict` mapping `Species` to their first three ionization energies, defaults to `Korg.ionization_energies`.
  * `partition_funcs`, a `Dict` mapping `Species` to partition functions (in terms of ln(T)). Defaults to data from Barklem & Collet 2016, `Korg.default_partition_funcs`.
  * `equilibrium_constants`, a `Dict` mapping `Species` representing diatomic molecules to the base-10 log of their molecular equilibrium constants in partial pressure form.  Defaults to data from Barklem and Collet 2016, `Korg.default_log_equilibrium_constants`.
  * `use_chemical_equilibrium_from` (default: `nothing`): Takes another solution returned by `synthesize`. When provided, the chemical equilibrium solution will be taken from this object, rather than being recomputed. This is physically self-consistent only when the abundances, `A_X`, and model atmosphere, `atm`, are unchanged.
  * `molecular_cross_sections` (default: `[]`): A vector of precomputed molecular cross-sections. See [`MolecularCrossSection`](@ref) for how to generate these. If you are using the default radiative transfer scheme, your molecular cross-sections should cover 5000 Å only if your linelist does.
  * `tau_scheme` (default: "linear"): how to compute the optical depth.  Options are "linear" and "bezier" (testing only–not recommended).
  * `I_scheme` (default: `"linear_flux_only"`): how to compute the intensity.  Options are `"linear"`, `"linear_flux_only"`, and `"bezier"`.  `"linear_flux_only"` is the fastest, but does not return the intensity values anywhere except at the top of the atmosphere.  "linear" performs an equivalent calculation, but stores the intensity at every layer. `"bezier"` is for testing and not recommended.
  * `verbose` (default: `false`): Whether or not to print information about progress, etc.
