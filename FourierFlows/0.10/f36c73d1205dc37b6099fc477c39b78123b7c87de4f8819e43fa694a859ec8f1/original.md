```
mutable struct Diagnostic{T, N} <: AbstractDiagnostic
```

A diagnostic that includes `N` elements of type `T`.

  * `calc::Function`: function that returns the diagnostic via `calc(prob)`
  * `prob::FourierFlows.Problem`: the relevant problem for this diagnostic
  * `data::Vector`: vector where the diagnostic time-series is saved
  * `t::Vector{Float64}`: vector with the times for which the diagnostic was saved
  * `steps::Vector{Int64}`: vector with the problem's `step` for which the diagnostic was saved
  * `freq::Int64`: integer denoting how often (every how many `problem.step`s) to save the diagnostic
  * `i::Int64`: integer denoting how many times the `diagnostic.data` was updated
