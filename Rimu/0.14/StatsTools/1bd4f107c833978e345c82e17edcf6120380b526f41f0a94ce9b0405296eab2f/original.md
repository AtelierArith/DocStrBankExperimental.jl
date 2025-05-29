```
shift_estimator(df::DataFrame; shift=:shift, kwargs...)
shift_estimator(sim::PMCSimulation; kwargs...)
-> r::BlockingResult
```

Return the shift estimator from the data in `df.shift`. The keyword argument `shift` can be used to change the name of the relevant column. Other keyword arguments are passed on to [`blocking_analysis`](@ref). Returns a [`BlockingResult`](@ref).

See also [`growth_estimator`](@ref), [`projected_energy`](@ref).
