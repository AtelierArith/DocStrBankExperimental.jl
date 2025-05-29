```
`ccf_1D!(ccf_out, ccf_var_out, λs, fluxes, var; ccf_plan )`
```

Compute the cross correlation function of a spectrum with a mask.     Generalized version that should work with different mask shapes.

# Inputs:

  * `ccf_out`: 1-d array of size length(calc*ccf*v_grid(plan)) to store output
  * `ccf_var_out`:  1-d array of size length(calc*ccf*v_grid(plan)) to store output
  * `λs`: 1-d array of wavelengths
  * `fluxes`:  1-d array of fluxes
  * `var`:  1-d array of flux variances

# Optional Arguments:

  * `plan`:  parameters for computing ccf (BasicCCFPlan())
