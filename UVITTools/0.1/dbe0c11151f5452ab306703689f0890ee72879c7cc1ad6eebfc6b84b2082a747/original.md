```
fuv_grating1_fluxed_spec(target,fuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, angle_xaxis_disp_deg=0.0, cross_disp_width_pixels = 40])
```

Extract flux calibrated spectrum from AstroSat/UVIT FUV-Grating1 dispersed image generated from CCDLAB processing pipeline.

This is a main function that uses other functions for extraction of source and background spectra, wavelenth  	and flux calibrations, and outputs fluxed spectrum. For details on grating orders, wavelength and flux calibrations,  	see [Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract). ...

# Arguments

## Required parameters

  * `target::String`: Name of the target available in the observed UVIT field.
  * `fuv_grating1_image_file::String`: Name of the FUV-Grating1 image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum. Allowed orders=-1 and -2.
  * `angle_xaxis_disp_deg::Float64`: 0.0 (default), angle between dispersion axis and x-axis.
  * `cross_disp_width_pixels::String`: 40 (default), width in pixels in the cross-dispersion direction.

## Output

  * `(λ, f_λ, err_f_λ)`
  * Fluxed spectrum saved in an ascii file.
  * DS9 source and background region files used for spectral extraction.
  * Source and background count spectral data in ascii files
  * Net source count spectrum in ascii file

...
