```
GeneratorStorageAvailability
```

The `GeneratorStorageAvailability` result specification reports the sample-level discrete availability of `GeneratorStorages`, producing a `GeneratorStorageAvailabilityResult`.

A `GeneratorStorageAvailabilityResult` can be indexed by generator-storage name and timestamp to retrieve a vector of sample-level availability states for the unit in the given timestep. States are provided as a boolean with `true` indicating that the unit is available and `false` indicating that it's unavailable.

Example:

```julia
genstoravail, =
    assess(sys, SequentialMonteCarlo(samples=10), GeneratorStorageAvailability())

samples = genstoravail["MyGenerator123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Bool}
@assert length(samples) == 10
```
