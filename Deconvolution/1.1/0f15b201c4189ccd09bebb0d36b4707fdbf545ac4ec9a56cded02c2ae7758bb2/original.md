```
lucy(observed, psf[, iterations])
```

Returns the Richardson-Lucy deconvolution of `observed`, using the point spread function `psf`.

All arguments must be arrays in the time/space domain and all of the same size, they will be converted into the frequency domain internally using the `fft` function.
