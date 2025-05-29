```
ShortfallSamples
```

The `ShortfallSamples` result specification reports sample-level unserved energy outcomes, producing a `ShortfallSamplesResult`.

A `ShortfallSamplesResult` can be directly indexed by a region name and a timestamp to retrieve a vector of sample-level unserved energy results in that region and timestep. [`EUE`](@ref) and [`LOLE`](@ref) constructors can also be used to retrieve standard risk metrics.

Example:

```julia
shortfall, =
    assess(sys, SequentialMonteCarlo(samples=10), ShortfallSamples())

period = ZonedDateTime(2020, 1, 1, 0, tz"UTC")

samples = shortfall["Region A", period]

@assert samples isa Vector{Float64}
@assert length(samples) == 10

# System-wide risk metrics
eue = EUE(shortfall)
lole = LOLE(shortfall)
neue = NEUE(shortfall)

# Regional risk metrics
regional_eue = EUE(shortfall, "Region A")
regional_lole = LOLE(shortfall, "Region A")
regional_neue = NEUE(shortfall, "Region A")

# Period-specific risk metrics
period_eue = EUE(shortfall, period)
period_lolp = LOLE(shortfall, period)

# Region- and period-specific risk metrics
period_eue = EUE(shortfall, "Region A", period)
period_lolp = LOLE(shortfall, "Region A", period)
```

Note that this result specification requires large amounts of memory for larger sample sizes. See [`Shortfall`](@ref) for average shortfall outcomes when sample-level granularity isn't required.
