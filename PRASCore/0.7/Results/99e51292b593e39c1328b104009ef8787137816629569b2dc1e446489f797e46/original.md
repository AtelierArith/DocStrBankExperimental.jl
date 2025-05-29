```
Flow
```

The `Flow` result specification reports the estimated average flow across transmission `Interfaces`, producing a `FlowResult`.

A `FlowResult` can be indexed by a directional `Pair` of region names and a timestamp to retrieve a tuple of sample mean and standard deviation, estimating the average net flow magnitude and direction relative to the given directed interface in that timestep. For a query of `"Region A" => "Region B"`, if estimated average flow was from A to B, the reported value would be positive, while if average flow was in the reverse direction, from B to A, the value would be negative.

Example:

```julia
flows, =
    assess(sys, SequentialMonteCarlo(samples=1000), Flow())

flow_mean, flow_std =
    flows["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
flow2_mean, flow2_std =
    flows["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]
@assert flow_mean == -flow2_mean
```

See [`FlowSamples`](@ref) for sample-level flow results.
