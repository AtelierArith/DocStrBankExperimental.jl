```
`ccf_1D!(ccf_out, ccf_covar_out, λs, fluxes, var; ccf_plan )`
```

Compute the cross correlation function of a spectrum with a mask.     Generalized version that should work with different mask shapes.     WIP:  Generalized version to compute covariance matrix for ccf and optionally to account for LSF

# Inputs:

  * `ccf_out`: 1-d array of size length(calc*ccf*v_grid(plan)) to store output
  * `ccf_covar_out`:  2-d array of size length(calc*ccf*v_grid(plan))^2 to store output
  * `λs`: 1-d array of wavelengths
  * `fluxes`:  1-d array of fluxes
  * `var`:  1-d array of flux variances

# Optional Arguments:

  * `plan`:  parameters for computing ccf (BasicCCFPlan())
