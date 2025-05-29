```
plotcoh(model)
plotcoh!(model)
plotcoh(model, Ω)
plotcoh!(model, Ω)
```

Plot the coherance and group delay of a model at the frequencies `Ω`.  If multivariate, above the diagonal is the coherance, and below is the group delay and on the diagonal is the spectral density function. By default, `Ω = range(-π,π,length=200)` and `Δ = 1`.
