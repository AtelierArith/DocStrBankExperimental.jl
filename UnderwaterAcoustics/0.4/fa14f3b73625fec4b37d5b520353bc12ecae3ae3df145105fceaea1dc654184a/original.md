```
absorption(frequency, distance=1000, salinity=35, temperature=27, depth=0, pH=8.1)
```

Compute volume acoustic absorption coefficient in water, given:

  * `frequency` in Hz
  * `distance` in meters
  * `salinity` in ppt
  * water `temperature` in °C
  * `depth` in meters
  * `pH` of water

The result is a unitless linear scale factor for sound pressure over the given `distance`. To get absorption in terms of dB / m, set `distance = 1.0` and convert the result to decibels. For instance, at a frequency of 100 kHz:

```julia-repl
julia> A = absorption(100e3, 1.0)
0.9959084838594522

julia> α = -20log10(A)
0.035611359656810865
```

Implementation based on the Francois and Garrison (1982) model.
