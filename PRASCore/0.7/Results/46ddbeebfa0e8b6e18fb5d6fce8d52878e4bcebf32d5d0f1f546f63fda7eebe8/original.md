```
Utilization
```

The `Utilization` result specification reports the estimated average absolute utilization of `Interfaces`, producing a `UtilizationResult`.

Whereas `Flow` reports the average directional power transfer across an interface, `Utilization` reports the absolute value of flow relative to the interface's transfer capability (counting the effects of line outages). For example, a symmetrically-constrained interface which is fully congested with max power flowing in one direction in half of the samples, and the other direction in the remaining samples, would have an average flow of 0 MW, but an average utilization of 100%.

A `UtilizationResult` can be indexed by a `Pair` of region names and a timestamp to retrieve a tuple of sample mean and standard deviation, estimating the average utilization of the interface. Given the absolute value nature of the outcome, results are independent of direction. Querying `"Region A" => "Region B"` will yield the same result as `"Region B" => "Region A"`.

Example:

```julia
utils, =
    assess(sys, SequentialMonteCarlo(samples=1000), Utilization())

util_mean, util_std =
    utils["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

util2_mean, util2_std =
    utils["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert util_mean == util2_mean
```

See [`UtilizationSamples`](@ref) for sample-level utilization results.
