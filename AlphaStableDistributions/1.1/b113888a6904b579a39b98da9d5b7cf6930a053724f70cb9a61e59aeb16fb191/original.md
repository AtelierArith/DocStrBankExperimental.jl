```
fit(d::Type{<:AlphaStable}, x; alg=QuickSort)
```

Fit an α stable distribution to data.

returns `AlphaStable`

α∈[0.6,2.0], β∈[-1,1] , c∈[0,∞] and δ∈[-∞,∞] are the characteristic exponent,  skewness parameter, scale parameter (dispersion^1/α) and location parameter respectively.

α, β, c and δ are computed based on McCulloch (1986) fractile.
