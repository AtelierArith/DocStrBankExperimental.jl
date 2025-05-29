```
StorageEnergy
```

The `StorageEnergy` result specification reports the average state of charge of `Storages`, producing a `StorageEnergyResult`.

A `StorageEnergyResult` can be indexed by storage device name and a timestamp to retrieve a tuple of sample mean and standard deviation, estimating the average energy level for the given storage device in that timestep.

Example:

```julia
storenergy, =
    assess(sys, SequentialMonteCarlo(samples=1000), StorageEnergy())

soc_mean, soc_std =
    storenergy["MyStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
```

See [`StorageEnergySamples`](@ref) for sample-level storage states of charge.

See [`GeneratorStorageEnergy`](@ref) for average generator-storage states of charge.
