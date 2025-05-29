```
predict(m,newcovars; <keyword arguments>)
```

Predict counts using a fitted HDMRPaths object and given newcovars.

# Example:

```julia
  m = fit(HDMRPaths,covars,counts)
  newcovars = covars[1:10,:]
  countshat = predict(m, newcovars; select=MinAICc())
```

# Arguments

  * `m::HDMRPaths` fitted DMRPaths model (HDMRCoefs currently not supported)
  * `newcovars` n-by-p matrix of covariates of same dimensions used to fit m.

# Keywords

  * `select=MinAICc()` See [`coef(::RegularizationPath)`](@ref).
  * `kwargs...` additional keyword arguments passed along to predict() for each category j=1..size(counts,2)
