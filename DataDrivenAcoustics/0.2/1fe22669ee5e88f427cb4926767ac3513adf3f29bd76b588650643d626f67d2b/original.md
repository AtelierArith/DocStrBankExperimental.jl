```julia
arrivals(model, tx, rx; threshold)

```

Show arrival rays at a location `rx` using a data-driven physics-based propagation model.

  * `model`: data-driven physics-based propagation model
  * `tx`: acoustic source. This is optional. Use `missing` or `nothing` for unknown source.
  * `rx`: an acoustic receiver
