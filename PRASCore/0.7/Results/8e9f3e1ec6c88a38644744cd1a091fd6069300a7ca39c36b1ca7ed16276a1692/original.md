```
SurplusSamples
```

The `SurplusSamples` result specification reports sample-level unused generation and storage discharge capability of `Regions`, producing a `SurplusSamplesResult`.

A `SurplusSamplesResult` can be indexed by region name and timestamp to retrieve a vector of sample-level surplus values in that region and timestep.

Example:

```julia
surplus, =
    assess(sys, SequentialMonteCarlo(samples=10), SurplusSamples())

samples = surplus["Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10
```

Note that this result specification requires large amounts of memory for larger sample sizes. See [`Surplus`](@ref) for estimated average surplus values when sample-level granularity isn't required.
