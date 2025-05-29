```
GeneratorStorageEnergy
```

The `GeneratorStorageEnergy` result specification reports the average state of charge of `GeneratorStorages`, producing a `GeneratorStorageEnergyResult`.

A `GeneratorStorageEnergyResult` can be indexed by generator-storage device name and a timestamp to retrieve a tuple of sample mean and standard deviation, estimating the average energy level for the given generator-storage device in that timestep.

Example:

```julia
genstorenergy, =
    assess(sys, SequentialMonteCarlo(samples=1000), GeneratorStorageEnergy())

soc_mean, soc_std =
    genstorenergy["MyGeneratorStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
```

See [`GeneratorStorageEnergySamples`](@ref) for sample-level generator-storage states of charge.

See [`StorageEnergy`](@ref) for average storage states of charge.
