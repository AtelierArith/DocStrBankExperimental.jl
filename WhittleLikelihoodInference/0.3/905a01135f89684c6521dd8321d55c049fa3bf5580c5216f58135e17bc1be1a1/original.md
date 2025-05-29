```
plotsdf(model)
plotsdf!(model)
plotsdf(model, Ω)
plotsdf!(model, Ω)
```

Plot the spectral density function of a model at the frequencies `Ω`.  By default, `Ω = range(-π,π,length=200)` and `Δ = 1`.
