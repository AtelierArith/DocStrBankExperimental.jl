```
LazyNBProportionalBandSpectrum{NO,IsTonal}(TBands::Type{<:AbstractProportionalBands{NO}}, f1_nb, df_nb, msp_amp, scaler=1)
```

Construct a lazy representation of a proportional band spectrum with proportional band type `TBands` from a narrowband spectrum.

The narrowband frequencies are defined by the first narrowband frequency `f1_nb` and the narrowband frequency spacing `df_nb`. `msp_amp` is the spectrum of narrowband mean squared pressure amplitude. The proportional band frequencies will be scaled by `scaler`.

`IsTonal` is a `Bool` indicating how the acoustic energy is distributed through the narrow frequency bands:

  * `IsTonal == false` means the acoustic energy is assumed to be evenly distributed thoughout each band
  * `IsTonal == true` means the acoustic energy is assumed to be concentrated at each band center
