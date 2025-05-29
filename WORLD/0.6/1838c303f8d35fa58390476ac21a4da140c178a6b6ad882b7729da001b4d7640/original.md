```julia
code_aperiodicity(aperiodicity, fs)
code_aperiodicity(aperiodicity, fs, fftsize)

```

CodeAperiodicity codes the aperiodicity. The number of dimensions is determined by fs.

**Parameters**

  * `aperiodicity` : Aperiodicity before coding
  * `fs` : Sampling frequency
  * `fftsize` : FFT size (default : `get_fftsize_for_cheaptrick(fs)`)

**Returns**

  * `coded_aperiodicity` : Coded aperiodicity
