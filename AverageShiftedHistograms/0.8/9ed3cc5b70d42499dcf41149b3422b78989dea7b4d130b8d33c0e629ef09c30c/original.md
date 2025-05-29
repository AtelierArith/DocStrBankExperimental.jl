# Univariate Ash

```
ash(x; kw...)
```

Fit an average shifted histogram to data `x`.

```
ash(x, weight::AbstractWeights; kw...)
```

Fit a weighted average shifted histogram to data `x`.

Keyword options are:

  * `rng`    : values over which the density will be estimated
  * `m`      : Number of adjacent histograms to smooth over
  * `kernel` : kernel used to smooth the estimate

# Bivariate Ash

```
ash(x, y; kw...)
```

Fit a bivariate averaged shifted histogram to data vectors `x` and `y`.  Keyword options are:

  * `rngx`    : x values where density will be estimated
  * `rngy`    : y values where density will be estimated
  * `mx`      : smoothing parameter in x direction
  * `my`      : smoothing parameter in y direction
  * `kernelx` : kernel in x direction
  * `kernely` : kernel in y direction

# Mutating an Ash object

Ash objectes can be updated with new data, new weights(only for univariates), smoothing parameter(s), or kernel(s).  They cannot, however, change the ranges over which the density is estimated.  It is therefore suggested to err on the side of caution when choosing data endpoints.

```
# univariate
ash!(obj; kw...)
ash!(obj, newx; kw...)
ash!(obj, newx, weight::AbstractWeights; kw...)

# bivariate
ash!(obj; kw...)
ash!(obj, newx, newy; kw...)
```
