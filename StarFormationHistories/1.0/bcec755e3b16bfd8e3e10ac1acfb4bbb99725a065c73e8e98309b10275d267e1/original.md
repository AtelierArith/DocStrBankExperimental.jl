```
mean(imf::Distributions.ContinuousUnivariateDistribution; kws...) =
    quadgk(x->x*pdf(imf,x), extrema(imf)...; kws...)[1]
```

Simple one-liner that calculates the mean of the provided `imf` distribution using numerical integration via `QuadGK.quadgk` with the passed keyword arguments `kws...`. This is a generic fallback; better to define this explicitly for your IMF model. Requires that `pdf(imf,x)` and `extrema(imf)` be defined.
