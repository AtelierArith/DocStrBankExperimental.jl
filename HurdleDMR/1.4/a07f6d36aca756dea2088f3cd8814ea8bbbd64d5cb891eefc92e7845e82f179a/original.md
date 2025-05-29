```
coef(m::DMRCoefs)
```

Returns the coefficient matrices fitted with DMR using the segment selected during fit (MinAICc by default).

# Example:

```julia
  m = fit(DMR,covars,counts)
  coef(m)
```
