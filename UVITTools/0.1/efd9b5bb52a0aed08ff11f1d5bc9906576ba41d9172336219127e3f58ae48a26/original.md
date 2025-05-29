`fuv_grating2_wavelength_calib(pixels, netsrc_spec_counts_per_s[, order = -2])`

Convert pixel numbers relative to zero to wavelengths.

This function is used for wavelength calibration of FUV-Grating2 count spectrum.

...

# Arguments

## Required parameters

  * `pixels::Array`: An array of pixel numbers relative to zero order.
  * `netsrc_spec_counts_per_s::Array`: An array of net count rates corresponding to the relative pixel numbers.

## Optional parameters

  * `order::Int`: -2 (default), Grating order. Allowed orders=-1 and -2.

...
