```
`ccf_1D( λs, fluxes, vars; ccf_plan )`
```

Compute the cross correlation function of a spectrum with a mask and its variance^1. ^1 = This version computes the diagonal terms for the ccf variance and neglects covariances due to the line spread function. Can roughly compensate by scaling up the ccf*var*scale from the default of 1. WARNING: Still needs more testing.

# Inputs:

  * `λs`: 1-d array of wavelengths
  * `fluxes`:  1-d array of fluxes

# Optional Arguments:

  * `ccf_plan`:  parameters for computing ccf (BasicCCFPlan())

# Returns:

  * 1-d array of size length(calc*ccf*v_grid(plan))
