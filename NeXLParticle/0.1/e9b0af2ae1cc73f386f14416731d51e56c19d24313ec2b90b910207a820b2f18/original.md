```
residual(zep::Zeppelin, row::Int, withImgs=false)::Union{Spectrum,Missing}
```

Returns the residual spectrum for the particle at `row` or missing if it does not exist. Never returns images.
