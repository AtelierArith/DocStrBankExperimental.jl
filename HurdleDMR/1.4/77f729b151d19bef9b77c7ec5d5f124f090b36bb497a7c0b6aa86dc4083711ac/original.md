```
coef(m::HDMRCoefs)
```

Returns the coefficient matrices fitted with HDMR using the segment selected during fit (MinAICc by default).

# Example:

```julia
  m = fit(HDMR,covars,counts)
  coefspos, coefszero = coef(m)
```
