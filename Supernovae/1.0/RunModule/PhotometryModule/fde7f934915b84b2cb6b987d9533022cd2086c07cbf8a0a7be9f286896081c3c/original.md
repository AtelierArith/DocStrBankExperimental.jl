```
flux_to_mag(flux::Unitful.Quantity{Float64}, zeropoint::Level)
```

Convert `flux` to magnitudes. Calculates `zeropoint - 2.5log10(flux)`. Returns `AB_mag` units

# Arguments

  * `flux::Unitful.Quantity{Float64}`: The flux to convert, in units compatible with Jansky. If the flux is negative it will be set to 0.0 to avoid `log10` errors
  * `zeropoint::Level`: The assumed zeropoint, used to convert the flux to magnitudes.
