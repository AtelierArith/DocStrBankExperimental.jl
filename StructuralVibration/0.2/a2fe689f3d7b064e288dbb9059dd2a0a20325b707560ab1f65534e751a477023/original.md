```
welch(input_signal, bs::Int, window = hanning(bs); fs::Int = 1,
      overlap = 0.5, scaling = :psd)
```

Estimation of one-sided Autopower functions of a signal using the Welch method

**Inputs**

  * `input_signal::Vector{Real}`: Input signal
  * `bs::Int`: Block size
  * `window`: Window function
  * `fs::Int`: Sampling rate
  * `overlap`: Overlap ratio between the segments
  * `scaling`: Scale of the PSD - see https://community.sw.siemens.com/s/article/the-autopower-function-demystified for more information

      * `:psd` (default) - Power Spectral Density
      * `:esd` - Autopower Energy Spectral Density
      * `:spectrum` - Autopower spectrum
      * `:linear` - Autopower linear

**Outputs**

  * `pxx`: Autopower
  * `freq`: Frequency range

**Available window functions**

**From DSP.jl**

  * `rect`
  * `hann` (default)
  * `hamming`
  * `tukey`
  * `cosine`
  * `lanczos`
  * `triang`
  * `bartlett`
  * `gaussian`
  * `bartlett_hann`
  * `blackman`
  * `kaiser`
  * `dpss`

**From StructuralVibration.jl**

  * `exponential`
  * `force`
  * `flattop`
  * `nutall`
  * `blackman_nutall`
  * `blackman_harris`
  * `parzen`
  * `planck`

**Note** The welch function is already implemented in `DSP.jl` under the name `welch_pgram`. The function `welch` is implemented here for pedagogical purposes.
