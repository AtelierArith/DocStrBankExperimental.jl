```
TFTDIAAFT(fϵ = 0.05; M::Int = 100, tol::Real = 1e-6, W::Int = 75)
```

[`TFTDIAAFT`](@ref)[^Lucio2012] are similar to [`TFTDAAFT`](@ref), but adds an iterative procedure to better match the periodograms of the surrogate and the original time series, analogously to how [`IAAFT`](@ref) improves upon [`AAFT`](@ref).

`fϵ ∈ (0, 1]` is the fraction of the powerspectrum corresponding to the lowermost frequencies to be preserved. `M` is the maximum number of iterations. `tol` is the desired maximum relative tolerance between power spectra. `W` is the number of bins into which the periodograms are binned when comparing across iterations.

See also: [`TFTD`](@ref), [`TFTDAAFT`](@ref).

[^Lucio2012]: Lucio, J. H., Valdés, R., & Rodríguez, L. R. (2012). Improvements to surrogate data methods for nonstationary time series. Physical Review E, 85(5), 056202.
