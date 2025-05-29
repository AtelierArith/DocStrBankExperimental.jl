`fuv_grating2_count_spec(fuv_grating2_image_file, ds9regfile[, order = -2, disp_aligned_to_xaxis = false, angle_xaxis_disp_deg = 267.479, cross_disp_width_pixels = 40, rate = true])` 

Extract count rate spectrum from AstroSat/UVIT FUV-Grating2 dispersed image generated from CCDLAB processing pipeline.

...

# Arguments

## Required parameters

  * `fuv_grating2_image_file::String`: Name of the FUV-Grating2 image file in FITS format generated using CCDLAB.
  * `ds9regfile::String`: Name of the ds9 region file with center as the zero order position.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum.                 Allowed orders=-1 and -2.
  * `disp_aligned_to_xaxis`: false (default), true if the dispersion axis is rotated to align to x-axis in the detector coordinates, false if dispersion axis left unrotated.
  * `angle_xaxis_disp_deg`: 267.479 (default), the angle in degrees between dispersion direction (from zero to minus orders) and the x-axis.

```
	If the dispersion axis is left unrotated in the detector coordiantes, the default value should be appropriate. 
	If the dispersion axis is rotated to align to x-axis, the angle should be set to 180 or zero degrees.
```

  * `cross_disp_width_pixels::Int`: 40 (default), width in pixels in the cross-dispersion direction.
  * `rate::Bool`: true (default) for count rate spectrum, otherwise false for count spectrum.

## Output

  * count spectrum file
  * region file compatible with ds9 that can be used to verify the extraction region.
  * Count spectrum as (pixel numbers relative to zero order, counts/s or counts, errors)

...
