```
StorageEnergySamples
```

The `StorageEnergySamples` result specification reports the sample-level state of charge of `Storages`, producing a `StorageEnergySamplesResult`.

A `StorageEnergySamplesResult` can be indexed by storage device name and a timestamp to retrieve a vector of sample-level charge states for the device in the given timestep.

Example:

```julia
storenergy, =
    assess(sys, SequentialMonteCarlo(samples=10), StorageEnergySamples())

samples = storenergy["MyStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10
```

Note that this result specification requires large amounts of memory for larger sample sizes. See [`StorageEnergy`](@ref) for estimated average storage state of charge when sample-level granularity isn't required.
