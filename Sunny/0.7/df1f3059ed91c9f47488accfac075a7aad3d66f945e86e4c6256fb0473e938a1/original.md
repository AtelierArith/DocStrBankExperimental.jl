```
gaussian(; {fwhm, σ})
```

Returns the function `exp(-x^2/2σ^2) / √(2π*σ^2)`. Either `fwhm` or `σ` must be specified, where `fwhm = (2.355...) * σ` is the full width at half maximum.
