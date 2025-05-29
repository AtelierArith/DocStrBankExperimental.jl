```
tfestimate(input_signal, output_signal, bs::Int, window_input = hanning(bs),
           window_output = window_input; fs::Int = 1, overlap = 0., type = :h1)
```

Estimation of the one-sided transfer function between two signals

**Inputs**

  * `input_signal::Vector{Real}`: Input signal
  * `output_signal::Vector{Real}`: Output signal
  * `bs::Int` Block size
  * `window_input`: Window function for the input signal
  * `window_output`: Window function for the output signal
  * `fs::Int`: Sampling rate
  * `overlap::Real`: Overlap ratio between the segments
  * `type::Symbol`: Type of transfer function to estimate

      * `:h1` (default)
      * `:h2`
      * `:h3` - h3 = (h1 + h2)/2
      * `:hv` - hv = sqrt(h1*h2)

**Outputs**

  * `H`: Transfer function
  * `freq`: Frequency range
  * `coh`: Coherence

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
  * `bartlett_hann`
  * `gaussian`
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
