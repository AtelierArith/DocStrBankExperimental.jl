```
LazyNBProportionalBandSpectrum(TBands::Type{<:AbstractProportionalBands}, f1_nb, df_nb, msp_amp, scaler=1, istonal::Bool=false)
```

Construct a `LazyNBProportionalBandSpectrum` using proportional bands `TBands` and narrowband mean squared pressure amplitude vector `msp_amp` and optional proportional band frequency scaler `scaler`.

`f1_nb` is the first non-zero narrowband frequency, and `df_nb` is the narrowband frequency spacing. The `istonal` `Bool` argument, if `true`, indicates the narrowband spectrum is tonal and thus concentrated at discrete frequencies. If `false`, the spectrum is assumed to be constant over each narrow frequency band. The proportional band frequencies will be scaled by `scaler`.
