```
waveband_conversion(;Itype = :direct, waveband = :PAR, mode = :power)
```

Returns the conversion coefficient from solar radiation (W/m2) to a give waveband in either power (W/m2) or photon flux (umol/m2/s). The coefficients are based on the Bird spectral model for a clear sky using June 21th in The Netherlands (latitude 52° N).

# Arguments

  * `Itype`: The type of solar radiation, either `:direct` or `:diffuse`.
  * `waveband`: The waveband of interest, one of `:PAR`, `:UV`, `:blue`, `:red`, `:green`, or `:NIR`.
  * `mode`: The physical units of the target, either `:power` (W/m^2) or `:flux` (umol/m^2/s).

# Examples

```julia
waveband_conversion(Itype = :diffuse, waveband = :UV, mode = :flux)
waveband_conversion(waveband = :NIR)
```
