```
interpolate_marcs(Teff, logg, A_X; kwargs...)
interpolate_marcs(Teff, logg, m_H=0, alpha_m=0, C_m=0; kwargs...)
```

Returns a model atmosphere computed by interpolating models from [MARCS](https://marcs.astro.uu.se/) ((Gustafsson+ 2008)[https://ui.adsabs.harvard.edu/abs/2008A&A...486..951G/abstract]). Along with `Teff` and `logg`, the atmosphere is specified by `m_H`, `alpha_m`, and `C_m`, which can be automatically determined from an `A_X` abundance vector (the recommended method, see [`format_A_X`](@ref)). Note that the MARCS atmosphere models were constructed with the Grevesse+ 2007 solar abundances (`Korg.grevesse_2007_solar_abundances`). This is handled automatically when `A_X` is provided.

`interpolate_marcs` uses three different interpolation schemes for different stellar parameter regimes. In the standard case the model atmosphere grid is [the one generated for SDSS](https://dr17.sdss.org/sas/dr17/apogee/spectro/speclib/atmos/marcs/MARCS_v3_2016/Readme_MARCS_v3_2016.txt), transformed and linearly interpolated. For cool dwarfs (`Teff` ≤ 4000 K, `logg` ≥ 3.5), the grid is resampled onto unchanging `tau_5000` values and interpolated with a cubic spline. For low-metallicity models (-5 ≤ `m_H` < -2.5), a grid of standard composition (i.e. fixed alpha and C) atmospheres is used.  (The microturbulence is 1km/s for dwarfs and 2km/s for giants and the mass for spherical models is 1 solar mass.) The interpolation method is the same as in the standard case. See [Wheeler+ 2024](https://ui.adsabs.harvard.edu/abs/2023arXiv231019823W/abstract) for more details and a discussion of errors introduced by model atmosphere interpolation. (Note that the cubic scheme for cool dwarfs is referred to as not-yet-implemented in the paper but is now available.)

# keyword arguments

  * `spherical`: whether or not to return a ShellAtmosphere (as opposed to a PlanarAtmosphere).  By default true when `logg` < 3.5.
  * `solar_abundances`: (default: `grevesse_2007_solar_abundances`) The solar abundances to use when `A_X` is provided instead of `M_H`, `alpha_M`, and `C_M`. The default is chosen to match that of the atmosphere grid, and if you change it you are likely trying to do something else.
  * `clamp_abundances`: (default: `false`) allowed only when specifying `A_X`. Whether or not to clamp the abundance parameters to be within range to avoid throwing an out of bounds error.
  * `perturb_at_grid_values` (default: `true`): whether or not to add or a subtract a very small number to each parameter which is exactly at a grid value. This prevents null derivatives, which can cause problems for minimizers.
  * `resampled_cubic_for_cool_dwarfs` (default: `true`): whether or not to used specialized method for cool dwarfs.
  * `archives`: A tuple containing the atmosphere grids to use.  For testing purposes.
