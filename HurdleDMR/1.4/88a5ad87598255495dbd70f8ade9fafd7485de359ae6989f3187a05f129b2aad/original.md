```
fit(DMRPaths,covars,counts; <keyword arguments>)
dmrpaths(covars,counts; <keyword arguments>)
```

Fit a Distributed Multinomial Regression (DMR) of counts on covars, and returns the entire regulatrization paths, which may be useful for plotting or picking coefficients other than the AICc optimal ones. Same arguments as [`fit(::DMR)`](@ref).
