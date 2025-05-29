```
Shortfall
```

The `Shortfall` result specification reports expectation-based resource adequacy risk metrics such as EUE and LOLE, producing a `ShortfallResult`.

A `ShortfallResult` can be directly indexed by a region name and a timestamp to retrieve a tuple of sample mean and standard deviation, estimating  the average unserved energy in that region and timestep. However, in most cases it's simpler to use [`EUE`](@ref) and [`LOLE`](@ref) constructors to directly retrieve standard risk metrics.

Example:

```julia
shortfall, =
    assess(sys, SequentialMonteCarlo(samples=1000), Shortfall())

period = ZonedDateTime(2020, 1, 1, 0, tz"UTC")

# Unserved energy mean and standard deviation
sf_mean, sf_std = shortfall["Region A", period]

# System-wide risk metrics
eue = EUE(shortfall)
lole = LOLE(shortfall)
neue = NEUE(shorfall)

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

See [`ShortfallSamples`](@ref) for recording sample-level shortfall results.
