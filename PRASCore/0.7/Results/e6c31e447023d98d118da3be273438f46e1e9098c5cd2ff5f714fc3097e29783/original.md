```
FlowSamples
```

The `FlowSamples` result specification reports the sample-level magnitude and direction of power flows across `Interfaces`, producing a `FlowSamplesResult`.

A `FlowSamplesResult` can be indexed by a directional `Pair` of region names and a timestamp to retrieve a vector of sample-level net flow magnitudes and directions relative to the given directed interface in that timestep. For a query of `"Region A" => "Region B"`, if flow in one sample was from A to B, the reported value would be positive, while if flow was in the reverse direction, from B to A, the value would be negative.

Example:

```julia
flows, =
    assess(sys, SequentialMonteCarlo(samples=10), FlowSamples())

samples = flows["Region A" => "Region B", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples isa Vector{Float64}
@assert length(samples) == 10

samples2 = flows["Region B" => "Region A", ZonedDateTime(2020, 1, 1, 0, tz"UTC")]

@assert samples == -samples2
```

Note that this result specification requires large amounts of memory for larger sample sizes. See [`Flow`](@ref) for estimated average flow results when sample-level granularity isn't required.
