```julia
transfercoef(model, tx, rx; mode)

```

Calculate transmission coefficient at location `rx` using a data-driven physics-based propagation model.

  * `model`: data-driven physics-based propagation model
  * `tx`: acoustic source. This is optional. Use `missing` or `nothing` for unknown source.
  * `rx`: acoustic receiver location(s)
