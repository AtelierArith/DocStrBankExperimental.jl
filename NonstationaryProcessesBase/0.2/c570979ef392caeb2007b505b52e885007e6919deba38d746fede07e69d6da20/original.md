```
Process(; process=nothing, process_kwargs...)
```

Define a `Process` that simulates a given system, specified by `process::Function`, and any simulation parameters (including control parameters, sampling parameters, solver parameters, and some metadata like the date and a simulation ID). For a complete list of `process_kwargs`, see the [`fieldguide`](@ref NonstationaryProcessesBase.fieldguide). A `Process` can also be used to create other `Process`es using the syntax `S = (P::Process)(;process_kwargs...)`, which will first copy `P` then update any fields given in `process_kwargs`
