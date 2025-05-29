```
make_generator_outage_draws!(
    sys,
    initial_time::Dates.DateTime=nothing,
    resolution::TIMEPERIOD=nothing,
    steps::Int=nothing,
    horizon::Int=nothing,
) where {TIMEPERIOD <: Dates.TimePeriod}
```

Adds availability time series to the generators in the system.

Main function to make generator outage draws.
