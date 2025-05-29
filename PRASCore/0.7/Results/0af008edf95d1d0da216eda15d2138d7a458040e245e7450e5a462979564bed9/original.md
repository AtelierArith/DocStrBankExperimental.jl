```
GeneratorAvailability
```

The `GeneratorAvailability` result specification reports the sample-level discrete availability of `Generators`, producing a `GeneratorAvailabilityResult`.

A `GeneratorAvailabilityResult` can be indexed by generator name and timestamp to retrieve a vector of sample-level availability states for the unit in the given timestep. States are provided as a boolean with `true` indicating that the unit is available and `false` indicating that it's unavailable.

Example:

```julia
genavail, =
    assess(sys, SequentialMonteCarlo(samples=10), GeneratorAvailability())

samples = genavail["MyGenerator123", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Bool}
@assert length(samples) == 10
```
