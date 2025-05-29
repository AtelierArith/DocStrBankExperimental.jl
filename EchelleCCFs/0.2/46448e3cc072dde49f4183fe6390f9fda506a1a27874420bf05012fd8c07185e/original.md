```
`ccf_1D( λs, fluxes; ccf_plan )`
Compute the cross correlation function of a spectrum with a mask.
```

# Inputs:

  * `λs`: 1-d array of wavelengths
  * `fluxes`:  1-d array of fluxes

# Optional Arguments:

  * `ccf_plan`:  parameters for computing ccf (BasicCCFPlan())

# Returns:

  * 1-d array of size length(calc*ccf*v_grid(plan))
