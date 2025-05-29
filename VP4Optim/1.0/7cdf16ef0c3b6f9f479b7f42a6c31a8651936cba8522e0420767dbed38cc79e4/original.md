```
par(mod::Model)
```

Returns *fixed* model parameters, according to the order specified in `mod.par_ind`.

## Default

  * Returns `mod.val[mod.par_ind]::Vector{Float64}`.
