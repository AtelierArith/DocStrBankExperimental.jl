`fuv_grating1_flux_calib(lamA, netsrc_spec_counts_per_s_A[,order=-2])`

Flux calibrate the wavelength-calibrated count spectrum from FUV-Grating1.

This function calculates the effective area at each wavelength of the count spectrum,  then uses the effective areas to convert net count rates to f_λ in CGS units.

...

# Arguments

## Required

-`lamA::Array{Float64}`: Array of wavelengths in Å. -`netsrc_spec_counts_per_s_A::Array{Float64}`: Array of background corrected counts/s/Å corresponding to wavelength array.

## Optional

-`Order::Number`: Grating order -2 (default) or -1.

...
