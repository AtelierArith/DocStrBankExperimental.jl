```
fuv_grating1_net_countrate_spec(fuv_grating1_image_file::String, ds9srcregfile::String, ds9bgdregfile::String; order::Int = -2, angle_xaxis_disp_deg::Float64=0.0, cross_disp_width_pixels::Int = 40)
```

`fuv_grating1_net_countrate_spec(fuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels = 40])` 

Extract background corrected, net count rate spectrum from AstroSat/UVIT FUV-Grating1 dispersed image generated from CCDLAB processing pipeline.

...

# Arguments

## Required parameters

  * `fuv_grating1_image_file::String`: Name of the FUV-Grating1 image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum.                 Allowed orders=-1 and -2.
  * `angle_xaxis_disp_deg`: 0.0 (default), angle between dispersion axis and x-axis.
  * `cross_disp_width_pixels::Int`: 40 (default), width in pixels in the cross-dispersion direction.

## Output

  * DS9 Region files used for extraction source and background count spectra.
  * Source and background count spectra in ascii files.

...
