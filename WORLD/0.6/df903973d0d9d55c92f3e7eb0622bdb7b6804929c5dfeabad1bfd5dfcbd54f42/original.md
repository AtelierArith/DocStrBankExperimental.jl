```julia
get_fftsize_for_cheaptrick(fs)
get_fftsize_for_cheaptrick(fs, opt)

```

GetFFTSizeForCheapTrick calculates the FFT size based on the sampling frequency and the lower limit of f0 (It is defined in world.h).

**Parameters**

  * `fs`: Sampling frequency
  * `opt`: CheapTrickOption

**Returns**

  * `fftsize` : FFT size
