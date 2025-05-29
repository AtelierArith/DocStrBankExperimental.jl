```julia
struct ParticleFilterMemory
```

Contains maximum memory for latent and observed data. Relevant for number of propagation steps from initial particle distribution and for first time particles are weighted with data point.

# Fields

  * `latent::Int64`: Latent variable memory. Number of times that initial particle distribution is used.
  * `data::Int64`: Observed data memory. First particle weighting taken at this point.
  * `initial::Int64`: Number of times when sampled from initial distribution. Per default equal to latent.
