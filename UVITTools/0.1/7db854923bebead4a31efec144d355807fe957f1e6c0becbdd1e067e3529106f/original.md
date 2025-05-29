```
nuv_grating_m1_fluxed_spec(target,nuv_grating_image_file, ds9srcregfile, ds9bgdregfile[,order=-1, cross_disp_width_pixels= 40, outfile="default"])
```

Extract flux calibrated spectrum from AstroSat/UVIT NUV-Grating order=-1 dispersed image generated from CCDLAB processing pipeline.

This is a main function that uses other functions for extraction of source and background spectra, wavelenth  	and flux calibrations, and outputs fluxed spectrum. For details on grating orders, wavelength and flux calibrations,  	see [Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract). ...

# Arguments

## Required parameters

  * `target::String`: Name of the target available in the observed UVIT field.
  * `nuv_grating_image_file::String`: Name of the NUV-Grating image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `order::Int`: -1 (default), Grating order to be used to extract the spectrum. Allowed orders=-1. Order=-2 is not yet calibrated.
  * `cross_disp_width_pixels::String`: 40 (default), width in pixels in the cross-dispersion direction.

-`outfile::String`:Name of the output file. A default file name based on the target name/grating will be generated if outfile="default".

## Output

  * `(λ, f_λ, err_f_λ)`
  * Fluxed spectrum saved in an ascii file.

...
