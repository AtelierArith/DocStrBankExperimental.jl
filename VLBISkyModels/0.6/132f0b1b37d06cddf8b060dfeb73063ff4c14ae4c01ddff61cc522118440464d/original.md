```
NFFTAlg
```

Uses a non-uniform FFT to compute the visibilitymap. You can optionally pass uv which are the uv positions you will compute the NFFT at. This can allow for the NFFT plan to be cached improving performance

# Fields

  * `padfac`: Amount to pad the image

  * `reltol`: relative tolerance of the NFFT

  * `precompute`: NFFT interpolation algorithm.

  * `fftflags`: Flag passed to inner AbstractFFT. The fastest FFTW is FFTW.MEASURE but takes the longest to precompute
