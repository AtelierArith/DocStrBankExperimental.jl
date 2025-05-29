```
uvit_filter2pha(target,imagefile, ds9srcregfile, ds9bgdregfile[,satu_corr=true, respdir=""/soft/astrosat/resp/uvit/"])
```

Extract XSPEC/Sherpa compatible source and background PHA spectral files from AstroSat/UVIT broadband image generated from CCDLAB processing pipeline.

This function extracts source and background counts using the DS9 region files and converts them into PHA spectral files. For details on grating orders  and spectral responses, see [Dewangan (2021)](https://ui.adsabs.harvard.edu/abs/2021JApA...42...49D/abstract).

...

# Arguments

## Required parameters

  * `target::String`: Name of the target available in the observed UVIT field.
  * `imagefile::String`: Name of the FUV or NUV image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file for source.
  * `ds9bgdregfile::String`: Name of the ds9 region file for background.

## Optional parameters

  * `satu_corr::Bool`: Apply saturation correction for point sources only if true (default).
  * `respdir::String`: Name of the directory containing the response matrices in the local machine. The response files can be downloaded from the GitHub page.

## Output

  * Source and background PHA files.
  * Some relevant information are also printed on the screen.

...
