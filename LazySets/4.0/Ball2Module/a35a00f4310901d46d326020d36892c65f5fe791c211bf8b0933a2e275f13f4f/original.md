# Extended help

```
sample(B::Ball2, [nsamples]::Int;
       [rng]::AbstractRNG=GLOBAL_RNG,
       [seed]::Union{Int, Nothing}=nothing)
```

### Algorithm

Random sampling with uniform distribution in `B` is computed using Muller's method of normalized Gaussians. This method requires the package `Distributions`. See [`_sample_unit_nball_muller!`](@ref) for implementation details.
