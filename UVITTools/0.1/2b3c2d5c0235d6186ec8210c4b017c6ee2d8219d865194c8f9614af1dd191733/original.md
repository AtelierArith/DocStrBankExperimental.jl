```
uvit_zp_uc(channel, uvit_filter)
```

Obtain the magnitude zero point and unit conversation factor for FUV or NUV channel in any filter.

This function is based on the calibration information from Tandon et al. (2017) and (2020).  	The function is used by `uvit_aphot.jl` to count rates to flux densities and magnitudes.

...

# Arguments

  * `channel::String`: UVIT channel either FUV or NUV.
  * `uvit_filter::String`: UVIT filter name. Different names can be used for the same filter e.g., "F1", "F148W", "CaF2-1".

...
