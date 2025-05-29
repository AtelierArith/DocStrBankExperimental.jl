```
PressureSpectrumAmplitude{IsEven,IsTonal,Tel} <: AbstractNarrowbandSpectrum{IsEven,IsTonal,Tel}
```

Representation of acoustic pressure amplitude as a function of narrowband frequency.

The `IsEven` parameter is a `Bool` indicating if the length of the spectrum is even or not, affecting how the Nyquist frequency is calculated. The `IsTonal` `Bool` parameter, if `true`, indicates the pressure spectrum is tonal and thus concentrated at discrete frequencies. If `false`, the spectrum is assumed to be constant over each frequency band.
