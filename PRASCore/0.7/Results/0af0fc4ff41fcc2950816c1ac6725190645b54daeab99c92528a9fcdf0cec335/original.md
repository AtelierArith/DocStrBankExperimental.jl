```
Surplus
```

The `Surplus` result specification reports unused generation and storage discharge capability of `Regions`, producing a `SurplusResult`.

A `SurplusResult` can be indexed by region name and timestamp to retrieve a tuple of sample mean and standard deviation, estimating the average unused capacity in that region and timestep.

Example:

```julia
surplus, =
    assess(sys, SequentialMonteCarlo(samples=1000), Surplus())

surplus_mean, surplus_std =
    surplus["Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
```

See [`SurplusSamples`](@ref) for sample-level surplus results.
