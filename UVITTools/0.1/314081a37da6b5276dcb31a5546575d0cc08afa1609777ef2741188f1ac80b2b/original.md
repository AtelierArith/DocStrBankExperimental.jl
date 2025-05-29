`nuv_grating_m1_count_spec(nuv_grating_image_file, ds9regfile[, cross_disp_width_pixels = 40, rate = true, outfile="nuv_grating_m1_count_spec.dat"])` 

Extract count rate spectrum from AstroSat/UVIT NUV-Grating dispersed image generated from CCDLAB processing pipeline.

...

# Arguments

## Required parameters

  * `nuv_grating_image_file::String`: Name of the NUV-Grating image file in FITS format generated using CCDLAB.
  * `ds9regfile::String`: Name of the ds9 region file with center as the zero order position.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum.                 Allowed orders=-1 and -2.
  * `cross_disp_width_pixels::String`: 40 (default), width in pixels in the cross-dispersion direction.
  * `rate::Bool`: true (default) for count rate spectrum, otherwise false for count spectrum.
  * `outfile::String`: Name of ascii output file name. Default file name: "`nuv_grating_m1_count_spec.dat`".

...
