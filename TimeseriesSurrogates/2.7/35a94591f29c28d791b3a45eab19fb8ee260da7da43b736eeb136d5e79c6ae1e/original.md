```
TFTDAAFT(fϵ = 0.05)
```

[`TFTDAAFT`](@ref)[^Lucio2012] are similar to [`TFTD`](@ref) surrogates, but also re-scales back to the original values of the time series. `fϵ ∈ (0, 1]` is the fraction of the powerspectrum corresponding to the lowermost frequencies to be preserved.

See also: [`TFTD`](@ref), [`TFTDIAAFT`](@ref).

[^Lucio2012]: Lucio, J. H., Valdés, R., & Rodríguez, L. R. (2012). Improvements to surrogate data methods for nonstationary time series. Physical Review E, 85(5), 056202.
