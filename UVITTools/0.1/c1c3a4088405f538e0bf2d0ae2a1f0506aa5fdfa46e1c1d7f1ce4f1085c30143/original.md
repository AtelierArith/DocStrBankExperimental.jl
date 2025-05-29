```
uvit_aphot(imagefile,ds9srcregion, ds9bgdregion[, satu_corr=true, mst_or_bjd="mst"])
```

Perform aperture photometry of a source present in an UVIT FUV/NUV FITS image  obtained from CCDLAB pipeline.

This function uses DS9 source and background region files and extracts count rates, corrects  	for any saturation, calculates the background net count rate, and then converts to  		flux density f_λ and AB magnitude using calibration  information available in  		[Tandon et al. (2020)](https://ui.adsabs.harvard.edu/abs/2020AJ....159..158T/abstract).

If the source region is a circle and satu*corr is true, then the source count rate is also corrected for saturation  using the function `uvit*saturation_corr.jl` (see below). For details,  	[see Tandon et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..128T/abstract).

...

# Arguments

## Required parameters

  * `imagefile::String`: Name of the FUV or NUV image file in FITS format generated using CCDLAB.
  * `ds9srcregfile::String`: Name of the ds9 region file for the source.
  * `ds9bgdregfile::String`: Name of the ds9 region file for background.

## Optional parameters

  * `satu_corr::Bool`: true (default), Apply saturation correction only if source extraction region is circular.   Valid for point sources only and if the redius of the circular extraction region is    about 29 pixels or 12 arcsec (see Tandon et al. 2020).
  * `mst_or_bjd::String`: Mission time or barycentric julian day, default: "mst".

...
