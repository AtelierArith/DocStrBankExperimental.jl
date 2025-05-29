```
Periodogram(timeseries, Δ)
```

Compute the periodogram for the provided timeseries with sampling rate Δ.

# Arguments

  * `timeseries`: A `Vector` if univariate and an `n` by `d` `Matrix` if multivariate, where `n` is the number of observations and `d` is the dimension of the timeseries.
  * `Δ`: A positive real number.

The periodogram is defined as

$$
\boldsymbol I(ω)&=\boldsymbol J(ω) \boldsymbol J(ω)^H \quad \text{where} \quad \boldsymbol J(ω) = \sqrt{\frac{Δ}{2π n}}\sum_{t=0}^{n-1} \boldsymbol{P}_{tΔ}e^{-itΔ ω}
$$

Note the periodogram is in terms of angular frequency here, and uses the normalisation $Δ/2π$. The choice of normalisation is essentially arbitrary; however, this matches our definition for the spectral density function.
