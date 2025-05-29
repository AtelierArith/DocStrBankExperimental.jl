```julia
cheaptrick(x, fs, timeaxis, f0; opt)

```

CheapTrick calculates the spectrogram that consists of spectral envelopes estimated by CheapTrick.

**Parameters**

  * `x` : Input signal
  * `fs` : Sampling frequency
  * `time_axis` : Time axis
  * `f0` : F0 contour
  * `opt` : CheapTrick option

**Returns**

  * `spectrogram`  : Spectrogram estimated by CheapTrick.
