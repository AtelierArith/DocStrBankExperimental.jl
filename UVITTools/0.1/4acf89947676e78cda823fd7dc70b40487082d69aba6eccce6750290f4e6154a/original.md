`fuv_grating1_count_spec(fuv_grating1_image_file, ds9regfile[, order = -1, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels = 40, rate = true])` 

Extract count rate spectrum from AstroSat/UVIT FUV-Grating1 dispersed image generated from CCDLAB processing pipeline.

...

# Arguments

## Required parameters

  * `fuv_grating1_image_file::String`: Name of the FUV-Grating1 image file in FITS format generated using CCDLAB.
  * `ds9regfile::String`: Name of the ds9 region file with center as the zero order position.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum.                 Allowed orders=-1 and -2.
  * `angle_xaxis_disp_deg`: 0.0 (default), angle between dispersion axis and x-axis.
  * `cross_disp_width_pixels::String`: 40 (default), width in pixels in the cross-dispersion direction.
  * `rate::Bool`: true (default) for count rate spectrum, otherwise false for count spectrum.

## Output

  * count spectrum file
  * region file compatible with ds9 that can be used to verify the extraction region for requested order.
  * Count spectrum as (pixel numbers relative to zero order, counts/s or counts, errors)

...
