```
peaktobackground(ffr::FilterFitResult, backwidth::Float64=10.0)::Float64
```

The peak-to-background ratio as determined from the raw and residual spectra integrated over the fit region-of-interest and scaled to `backwidth` eV of continuum (nominally 10 eV).
