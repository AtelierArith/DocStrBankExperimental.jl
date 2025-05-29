```
ecdf(X; weights::AbstractWeights)
```

Return an empirical cumulative distribution function (ECDF) based on a vector of samples given in `X`. Optionally providing `weights` returns a weighted ECDF.

Note: this function that returns a callable composite type, which can then be applied to evaluate CDF values on other samples.

`extrema`, `minimum`, and `maximum` are supported to for obtaining the range over which function is inside the interval $(0,1)$; the function is defined for the whole real line.
