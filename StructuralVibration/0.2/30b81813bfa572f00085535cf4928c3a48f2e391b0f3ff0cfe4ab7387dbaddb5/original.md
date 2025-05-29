```
spectrum(input_signal, bs::Int, window = hanning(bs); fs::Int = 1, 
         overlap = 0.5)
```

Estimation of the spectrum of a signal

**Inputs**

  * `input_signal::Vector{Real}`: Input signal
  * `bs::Int`: Block size
  * `window`: Window function
  * `fs::Int`: Sampling rate
  * `overlap`: Overlap ratio between the segments

**Outputs**

  * `y`: Signal spectrum
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
