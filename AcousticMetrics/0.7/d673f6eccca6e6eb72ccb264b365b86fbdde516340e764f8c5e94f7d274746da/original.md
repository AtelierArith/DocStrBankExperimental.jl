```
LazyNBProportionalBandSpectrum{NO,IsTonal,TF,TAmp,TBandsC}
```

Lazy representation of a proportional band spectrum with octave fraction `NO` and `eltype` `TF` constructed from a narrowband (`NB`) spectrum.

`IsTonal` indicates how the acoustic energy is distributed through the narrow frequency bands:

  * `IsTonal == false` means the acoustic energy is assumed to be evenly distributed thoughout each band
  * `IsTonal == true` means the acoustic energy is assumed to be concentrated at each band center
