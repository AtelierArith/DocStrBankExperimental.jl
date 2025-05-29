```julia
get_timestamps(
    result::PowerSimulations.SimulationProblemResults
) -> StepRange{Dates.DateTime, Dates.Millisecond}

```

利用可能なタイムスタンプのStepRangeへの参照を返します。
