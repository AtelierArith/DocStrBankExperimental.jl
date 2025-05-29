```
calz_unred(wave, flux, ebv[, r_v]) -> deredden_wave
```

### Purpose

Deredden a galaxy spectrum using the Calzetti et al. (2000) recipe.

### Explanation

Calzetti et al.  (2000, ApJ 533, 682; http://adsabs.harvard.edu/abs/2000ApJ...533..682C) developed a recipe for dereddening the spectra of galaxies where massive stars dominate the radiation output, valid between $0.12$ to $2.2$ microns.  (`calz_unred` extrapolates between $0.12$ and $0.0912$ microns.)

### Arguments

  * `wave`: wavelength (Angstroms)
  * `flux`: calibrated flux.
  * `ebv`: color excess E(B-V).  If a negative `ebv` is supplied, then fluxes will be reddened rather than deredenned.  Note that the supplied color excess should be that derived for the stellar continuum, EBV(stars), which is related to the reddening derived from the gas, EBV(gas), via the Balmer decrement by EBV(stars) = 0.44*EBV(gas).
  * `r_v` (optional): ratio of total to selective extinction, default is 4.05.  Calzetti et al. (2000) estimate $r_v = 4.05 ± 0.80$ from optical-IR observations of 4 starbursts.

### Output

Unreddened flux, same units as `flux`.  Flux values will be left unchanged outside valid domain ($0.0912$ - $2.2$ microns).

### Example

Estimate how a flat galaxy spectrum (in wavelength) between $1200 Å$ and $3200 Å$ is altered by a reddening of E(B-V) = 0.1.

```julia
wave = collect(1200:50:3150);
flux = ones(size(wave));
flux_new = calz_unred.(wave, flux, -0.1);
```

Using a plotting tool you can visualize the unreddend flux.  For example, with [Plots.jl](https://github.com/JuliaPlots/Plots.jl)

```julia
using Plots
plot(wave, flux_new)
```

### Notes

Code of this function is based on IDL Astronomy User's Library.
