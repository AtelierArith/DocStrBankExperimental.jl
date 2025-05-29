```
FINUFFTAlg
```

Uses the Flatiron non-uniform FFT FINUFFT to compute the visibilitymap.

# Fields

  * `padfac`: Amount to pad the image

  * `reltol`: relative tolerance of the NFFT (FINUFFT eps)

  * `threads`: how many threads to use

  * `fftflags`: Flag passed to inner AbstractFFT. The fastest FFTW is FFTW.MEASURE but takes the longest to precompute
