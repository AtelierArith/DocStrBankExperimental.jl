`fuv_grating2_net_countrate_spec(fuv_grating2_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, disp_aligned_to_xaxis=false, angle_xaxis_disp_deg=267.479, cross_disp_width_pixels = 40])` 

Extract background corrected, net count rate spectrum from AstroSat/UVIT FUV-Grating2 dispersed image generated from CCDLAB processing pipeline.

...

# Arguments

## Required parameters

  * `fuv_grating2_image_file::String`: Name of the FUV-Grating2 image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum.                 Allowed orders=-1 and -2.
  * `disp_aligned_to_xaxis`: false (default), true if the dispersion axis is rotated to align to x-axis in the detector coordinates, false if dispersion axis left unrotated.
  * `angle_xaxis_disp_deg`: 267.479 (default), the angle in degrees between dispersion direction (from zero to minus orders) and the x-axis.

```
	If the dispersion axis is left unrotated in the detector coordiantes, the default value should be appropriate. 
	If the dispersion axis is rotated to align to x-axis, the angle should be set to 180 or zero degrees.
```

  * `cross_disp_width_pixels::Int`: 40 (default), width in pixels in the cross-dispersion direction.

...
