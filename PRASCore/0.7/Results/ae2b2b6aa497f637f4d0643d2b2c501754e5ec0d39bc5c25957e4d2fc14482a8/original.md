```
GeneratorStorageEnergySamples
```

The `GeneratorStorageEnergySamples` result specification reports the sample-level state of charge of `GeneratorStorages`, producing a `GeneratorStorageEnergySamplesResult`.

A `GeneratorStorageEnergySamplesResult` can be indexed by generator-storage device name and a timestamp to retrieve a vector of sample-level charge states for the device in the given timestep.

Example:

```julia
genstorenergy, =
    assess(sys, SequentialMonteCarlo(samples=10), GeneratorStorageEnergySamples())

samples = genstorenergy["MyGeneratorStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10
```

Note that this result specification requires large amounts of memory for larger sample sizes. See [`GeneratorStorageEnergy`](@ref) for estimated average generator-storage state of charge when sample-level granularity isn't required.
