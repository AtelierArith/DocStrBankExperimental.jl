```
fuv_grating2_phafile(target,fuv_grating2_image_file, ds9srcregfile, ds9bgdregfile[, order = -2, disp_aligned_to_xaxis=false, angle_xaxis_disp_deg=267.479, cross_disp_width_pixels= 40])
```

Extract XSPEC/Sherpa compatible source and background PHA spectral files from AstroSat/UVIT FUV-Grating2 dispersed image generated from CCDLAB processing pipeline.

This function extracts source and background count spectra using the zero order positions provided  in the DS9 region files and converts them into PHA spectral files. For details on grating orders  and spectral responses, see [Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract).

...

# Arguments

## Required parameters

  * `target::String`: Name of the target available in the observed UVIT field.
  * `fuv_grating2_image_file::String`: Name of the FUV-Grating1 image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file with source center as the zero order position.
  * `ds9bgdregfile::String`: Name of the ds9 region file with  center in a source-free region of the image.

## Optional parameters

  * `order::Int`: -2 (default), Grating order to be used to extract the spectrum. Allowed orders=-1 and -2.
  * `disp_aligned_to_xaxis`: false (default), true if the dispersion axis is rotated to align to x-axis in the detector coordinates, false if dispersion axis left unrotated.
  * `angle_xaxis_disp_deg`: 267.479 (default), the angle in degrees between dispersion direction (from zero to minus orders) and the x-axis.

```
	If the dispersion axis is left unrotated in the detector coordiantes, the default value should be appropriate. 
	If the dispersion axis is rotated to align to x-axis, the angle should be set to 180 or zero degrees.
```

  * `cross_disp_width_pixels::Int`: 40 (default), width in pixels in the cross-dispersion direction.

## Output

  * Source and background PHA files.
  * Some relevant information are also printed on the screen.

...
