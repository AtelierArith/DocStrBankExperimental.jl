```
plotasdf(model)
plotasdf!(model)
plotasdf(model, Ω, Δ)
plotasdf!(model, Ω, Δ)
```

Plot the aliased spectral density function of a model at the frequencies Ω.  By default, `Ω = range(-π,π,length=200)` and `Δ = 1`.
