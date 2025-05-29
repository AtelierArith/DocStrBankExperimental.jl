```
x(mod::Model)
```

Returns *variable* model parameters, according to the order specified in `mod.x_ind`.

## Default

  * Returns `mod.val[mod.x_ind]::Vector{Float64}`.
