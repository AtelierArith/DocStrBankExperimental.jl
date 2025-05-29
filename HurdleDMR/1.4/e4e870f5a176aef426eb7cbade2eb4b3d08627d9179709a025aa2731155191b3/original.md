```
fit(HDMRPaths,covars,counts; <keyword arguments>)
hdmrpaths(covars,counts; <keyword arguments>)
```

Fit a Hurdle Distributed Multinomial Regression (HDMR) of counts on covars, and returns the entire regulatrization paths, which may be useful for plotting or picking coefficients other than the AICc optimal ones. Same arguments as [`fit(::HDMR)`](@ref).
