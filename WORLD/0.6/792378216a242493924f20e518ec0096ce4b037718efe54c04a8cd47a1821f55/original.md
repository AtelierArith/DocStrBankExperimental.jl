```julia
decode_aperiodicity(coded_aperiodicity, fs)
decode_aperiodicity(coded_aperiodicity, fs, fftsize)

```

DecodeAperiodicity decoes the coded aperiodicity.

**Parameters**

  * `coded_aperiodicity` : Coded aperiodicity
  * `fs` : Sampling frequency
  * `fftsize` : FFT size (default : `get_fftsize_for_cheaptrick(fs)`)

**Returns**

  * `aperiodicity` : Decoded aperiodicity
