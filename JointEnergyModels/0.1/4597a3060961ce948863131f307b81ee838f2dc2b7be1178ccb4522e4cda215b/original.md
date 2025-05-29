```
generate_samples(jem::JointEnergyModel, n::Int; kwargs...)
```

A convenience function for generating samples for a given energy model. If `n` is `missing`, then the sampler's `batch_size` is used.
