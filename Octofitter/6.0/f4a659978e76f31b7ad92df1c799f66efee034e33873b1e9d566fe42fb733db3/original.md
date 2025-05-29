```
Sine()
```

A custom univariate distribution. The pdf is a sine function defined between 0 and π. This is a common prior distribution used when fitting orbits to astrometry.

The full Distributions.jl interface is not yet defined for this distribution, but the following methods work: pdf, logpdf, minimum, maximum, insupport, mean, var, cdf, quantile
