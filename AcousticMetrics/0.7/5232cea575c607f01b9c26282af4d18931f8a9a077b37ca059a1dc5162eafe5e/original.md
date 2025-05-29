```
PowerSpectralDensityAmplitude(pth::AbstractPressureTimeHistory, hc=similar(pressure(pth)))
```

Construct a narrowband spectrum of the power spectral density amplitude from a pressure time history.

The optional argument `hc` will be used to store the discrete Fourier transform of the pressure time history, and should have length of `inputlength(pth)`.
