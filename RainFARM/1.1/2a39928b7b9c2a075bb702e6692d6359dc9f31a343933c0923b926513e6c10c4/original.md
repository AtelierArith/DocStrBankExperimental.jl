```
rainfarm(r,slope,nf,weight=1.;fglob=false, fsmooth=false, verbose=false)
```

Perform general RainFARM downscaling.

#Arguments

  * `r`      : large-scale array to downscale
  * `slope`  : spatial spectral slope
  * `nf`     : refinement factor for spatial downscaling
  * `weight` : weights for orographic downscaling
  * `fglob`  : conserve global average over domain
  * `fsmooth`: use smoothing instead of gp conservation
  * `verbose`: provide some progress report
