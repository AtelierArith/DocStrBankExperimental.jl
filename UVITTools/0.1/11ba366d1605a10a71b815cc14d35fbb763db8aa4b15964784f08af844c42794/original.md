`nuv_grating_m1_net_countrate_spec(nuv_grating_image_file, ds9srcregfile, ds9bgdregfile[, cross_disp_width_pixels = 40,  outfile="nuv_grating_m1_net_countrate_spec.dat"])` 

Extract background corrected, net count rate spectrum from AstroSat/UVIT NUV-Grating dispersed image generated from CCDLAB processing pipeline.

...

# Arguments

## Required parameters

  * `nuv_grating_image_file::String`: Name of the NUV-Grating image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `cross_disp_width_pixels::String`: 40 (default), width in pixels in the cross-dispersion direction.
  * `outfile::String`: Name of ascii output file name. Default file name: "`nuv_grating_m1_net_countrate_spec.dat`".

...
