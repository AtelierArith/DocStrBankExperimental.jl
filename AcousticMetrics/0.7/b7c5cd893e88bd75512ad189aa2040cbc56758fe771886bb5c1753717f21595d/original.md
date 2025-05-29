```
LazyNBProportionalBandSpectrum(f1_nb, df_nb, msp_amp, cbands::AbstractProportionalBands{NO,:center}, istonal=false)
```

Construct a lazy representation of a proportional band spectrum with proportional center bands `cbands` from a narrowband spectrum.

The narrowband frequencies are defined by the first narrowband frequency `f1_nb` and the narrowband frequency spacing `df_nb`. `msp_amp` is the spectrum of narrowband mean squared pressure amplitude.

`istonal` indicates how the acoustic energy is distributed through the narrow frequency bands:

  * `istonal == false` means the acoustic energy is assumed to be evenly distributed thoughout each band
  * `istonal == true` means the acoustic energy is assumed to be concentrated at each band center
