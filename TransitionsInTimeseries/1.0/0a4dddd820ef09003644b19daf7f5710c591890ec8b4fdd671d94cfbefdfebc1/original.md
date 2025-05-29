```
PrecomputedRidgeRegressionSlope
```

A struct containing the precomputed [ridge regression](https://en.wikipedia.org/wiki/Ridge_regression) matrix. Once `rrslope::PrecomputedRidgeRegressionSlope` is initialized, it can be used as a function to obtain the ridge regression slope of `x::AbstractVector` by applying:

```julia
rrslope(x)
```
