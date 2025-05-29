```
fit(d::Type{<:SymmetricAlphaStable}, x; alg=QuickSort)
```

Fit a symmetric α stable distribution to data.

returns `SymmetricAlphaStable`

α∈[1,2], c∈[0,∞] and δ∈[-∞,∞] are the characteristic exponent, scale parameter (dispersion^1/α) and location parameter respectively.

α is computed based on McCulloch (1986) fractile. scale is computed based on Fama & Roll (1971) fractile. location is the 50% trimmed mean of the sample.
