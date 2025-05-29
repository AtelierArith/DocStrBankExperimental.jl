```julia
code_spectral_envelope(
    spectrogram,
    fs,
    fftsize,
    number_of_dimentions
)

```

CodeSpectralEnvelope codes the spectral envelope.

**Parameters**

  * `spectrogram` : spectrogram (time sequence of spectral envelope)
  * `fs` : Sampling frequency
  * `fftsize` : FFT size
  * `number_of_dimentions` : Number of dimentions for coded spectral envelope

**Returns**

  * `coded_spectral_envelope` : Coded spectral envelope
