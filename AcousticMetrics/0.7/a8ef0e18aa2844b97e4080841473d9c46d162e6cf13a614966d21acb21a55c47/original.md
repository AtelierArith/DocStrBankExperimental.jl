```
PowerSpectralDensityAmplitude{IsEven,Tel} <: AbstractNarrowbandSpectrum{IsEven,false,Tel}
```

Representation of acoustic power spectral density amplitude as a function of narrowband frequency.

The `IsEven` parameter is a `Bool` indicating if the length of the spectrum is even or not, affecting how the Nyquist frequency is calculated. As the power spectral density is not well-defined for tones, the `IsTonal` parameter is always `false`.
