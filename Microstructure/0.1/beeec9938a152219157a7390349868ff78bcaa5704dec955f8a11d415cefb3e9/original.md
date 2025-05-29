```
test(mlp::Chain, data::Array{<:AbstractFloat,2}, ntest)
```

Return probabilistic estimates by applying a trained `mlp` to test data for `ntest` times with dropout layers on.

```
test(mlp::Chain, data::Array{<:AbstractFloat,2})
```

Get deterministic estimates with dropout layers off
