```
plotei(model)
plotei!(model)
plotei(model, n, Δ)
plotei!(model, n, Δ)
```

Plot the aliased spectral density function of a model at the angular Fourier frequencies `fftfreq(n,2π/Δ)`.  By default, `n = 1024` and `Δ = 1`.
