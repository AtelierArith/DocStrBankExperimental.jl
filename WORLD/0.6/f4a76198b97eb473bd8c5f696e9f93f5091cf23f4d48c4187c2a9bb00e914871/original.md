```julia
synthesis(f0, spectrogram, aperiodicity, period, fs, len)

```

Synthesis synthesize the voice based on f0, spectrogram and aperiodicity (not excitation signal.

**Parameters**

  * `f0` : f0 contour
  * `spectrogram` : Spectrogram estimated by CheapTrick
  * `aperiodicity` : Aperiodicity spectrogram based on D4C
  * `period` :  Temporal period used for the analysis
  * `fs` : Sampling frequency
  * `len` : Length of the output signal

**Returns**

  * `y` : Calculated speech
