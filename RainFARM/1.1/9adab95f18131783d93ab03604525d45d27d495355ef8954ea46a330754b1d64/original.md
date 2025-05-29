```
ww = rfweights(orofile, reffile, nf; weightsfn="", varname="", fsmooth=false)
```

Compute orographic weights from a fine-scale precipitation climatology file.

#Arguments

  * `orofile`  : filename of input climatology
  * `reffile`  : filename of reference file (for metadata, e.g. the file to downscale)
  * `nf`       : refinement factor for spatial downscaling
  * `weightsfn`: write weights to file weightsfn
  * `varname`  : variable name in climatology
  * `fsmooth`  : use smoothing instead of gp conservation

#Returns

  * `ww`       : a weight matrix also saved to weightsfn

#Depends

This function uses external system calls using the "cdo" command (https://code.mpimet.mpg.de/projects/cdo/wiki/Cdo) which needs to be available on your system.
