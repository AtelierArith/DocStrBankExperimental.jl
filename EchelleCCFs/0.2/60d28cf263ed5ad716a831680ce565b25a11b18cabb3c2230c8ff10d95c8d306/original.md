```
`ccf_1D( λs, fluxes; ccf_plan )`
Compute the cross correlation functions of spectra with a mask.
```

# Inputs:

  * `λs`: 1-d array of wavelengths
  * `fluxes`:  2-d array of fluxes, individual spectra along first dim

# Optional Arguments:

  * `ccf_plan`:  parameters for computing ccf (BasicCCFPlan())

# Returns:

  * 2-d array of size (length(calc*ccf*v_grid(plan)), size(flux, 2))
