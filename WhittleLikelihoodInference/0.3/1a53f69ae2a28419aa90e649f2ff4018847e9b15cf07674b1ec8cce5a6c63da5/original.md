```
plotacv(model)
plotacv!(model)
plotacv(model, τ)
plotacv!(model, τ)
plotacv(model, n, Δ)
plotacv!(model, n, Δ)
```

Plot the aliased spectral density function of a model at lags `τ`. If the model does not have known acv, then the number of lags `n` and sampling rate `Δ` should be provided. In this case, the lags are `-(n-1)*Δ:Δ:(n-1)*Δ`. If unprovided, `n = 30` and `Δ = 1`.
