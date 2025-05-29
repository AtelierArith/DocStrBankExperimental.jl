```
StorageAvailability
```

The `StorageAvailability` result specification reports the sample-level discrete availability of `Storages`, producing a `StorageAvailabilityResult`.

A `StorageAvailabilityResult` can be indexed by storage device name and a timestamp to retrieve a vector of sample-level availability states for the unit in the given timestep. States are provided as a boolean with `true` indicating that the unit is available and `false` indicating that it's unavailable.

Example:

```julia
storavail, =
    assess(sys, SequentialMonteCarlo(samples=10), StorageAvailability())

samples = storavail["MyStorage123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Bool}
@assert length(samples) == 10
```
