```julia
get_timestamps(
    result::PowerSimulations.SimulationProblemResults
) -> StepRange{Dates.DateTime, Dates.Millisecond}

```

Return a reference to a StepRange of available timestamps.
