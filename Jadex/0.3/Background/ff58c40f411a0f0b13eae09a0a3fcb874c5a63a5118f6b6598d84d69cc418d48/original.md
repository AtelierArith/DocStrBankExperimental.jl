```
BackgroundField(trj, backi, totalb)
```

# Arguments

  * `trj`: Background brightness temperature `[K]` in the Rayleigh-Jeans limit.
  * `backi`: Background intensity (integrated, $J_ν$) in `[erg / (s cm^2 Hz sr)]`.
  * `totalb`: Total background intensity. Note that because internal radiation           fields are not implemented, `totalb` should be identical to `backi`.
