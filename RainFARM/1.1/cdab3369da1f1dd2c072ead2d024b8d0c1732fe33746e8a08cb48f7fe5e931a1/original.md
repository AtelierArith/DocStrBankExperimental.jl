```
rf = downscale_spaceonly(r,f,weight=1.;fglob=false, fsmooth=false )
```

Downscale precipitation field `r` using metagaussian spectral field `f`. An optional weights array can be specified. Precipitation can be conserved globally (`fglob`) or using convolution (`fsmooth`).
