```
AbstractNarrowbandSpectrum{IsEven,IsTonal,Tel} <: AbstractVector{Tel}
```

Supertype for a generic narrowband acoustic metric which will behave as an immutable `AbstractVector` of element type `Tel`.

The `IsEven` parameter is a `Bool` indicating if the length of the spectrum is even or not, affecting how the Nyquist frequency is calculated. `IsTonal` indicates how the acoustic energy is distributed through the frequency bands:

  * `IsTonal == false` means the acoustic energy is assumed to be evenly distributed thoughout each band
  * `IsTonal == true` means the acoustic energy is assumed to be concentrated at each band center
