```
coef(m::HDMRPaths, select::SegSelect=MinAICc())
```

Returns all or selected coefficient matrices fitted with HDMR.

# Example:

```julia
  m = fit(HDMRPaths,covars,counts)
  coefspos, coefszero = coef(m, MinCVKfold{MinCVmse}(5))
```
