```
nuv_grating_phafile(target,nuv_grating1_image_file, ds9srcregfile, ds9bgdregfile[, cross_disp_width_pixels= 40])
```

Extract XSPEC/Sherpa compatible source and background PHA spectral files from AstroSat/UVIT NUV-Grating  dispersed image generated from CCDLAB processing pipeline.

This function extracts source and background count spectra using the zero order positions provided  in the DS9 region files and converts them into PHA spectral files. For details on grating orders  and spectral responses, see [Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract).

...

# Arguments

## Required parameters

  * `target::String`: Name of the target available in the observed UVIT field.
  * `nuv_grating_image_file::String`: Name of the NUV-Grating image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `cross_disp_width_pixels::String`: 40 (default), width in pixels in the cross-dispersion direction.
  * `respdir::String`: Name of the directory containing the response matrices in the local machine. The response files can be downloaded from the GitHub page.

#read necessary keywords`

## Output

  * Source and background PHA files.
  * Some relevant information are also printed on the screen.

...
