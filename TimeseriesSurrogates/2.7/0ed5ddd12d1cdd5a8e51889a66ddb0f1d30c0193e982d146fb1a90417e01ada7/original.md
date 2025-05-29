```
TFTD(phases::Bool = true, fϵ = 0.05)
```

The `TFTDRandomFourier` (or just `TFTD` for short) surrogate was proposed by Lucio et al. (2012)[^Lucio2012] as a combination of truncated Fourier surrogates[^Nakamura2006] ([`TFTS`](@ref)) and detrend-retrend surrogates.

The `TFTD` part of the name comes from the fact that it uses a combination of truncated Fourier transforms (TFT) and de-trending and re-trending (D) the time series before and after surrogate generation. Hence, it can be used to generate surrogates also from (strongly) nonstationary time series.

## Implementation details

Here, a best-fit linear trend is removed/added from the signal prior to and after generating the random Fourier signal. In principle, any trend can be removed, but so far, we only provide the linear option.

See also: [`TFTDAAFT`](@ref), [`TFTDIAAFT`](@ref).

[^Nakamura2006]: Nakamura, Tomomichi, Michael Small, and Yoshito Hirata. "Testing for nonlinearity in irregular fluctuations with long-term trends." Physical Review E 74.2 (2006): 026205.

[^Lucio2012]: Lucio, J. H., Valdés, R., & Rodríguez, L. R. (2012). Improvements to surrogate data methods for nonstationary time series. Physical Review E, 85(5), 056202.
