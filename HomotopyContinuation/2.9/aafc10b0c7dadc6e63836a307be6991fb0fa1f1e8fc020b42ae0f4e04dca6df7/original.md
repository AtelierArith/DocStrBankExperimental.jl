```
TrackerResult
```

Containing the result of tracking a path with a [`Tracker`](@ref).

## Fields

  * `return_code::Symbol`: A code indicating whether the tracking was successfull (`:success`). See [`TrackerCode`](@ref) for all possible values.
  * `solution::V`: The solution when the tracking stopped.
  * `t::ComplexF64`: The value of `t` when the tracking stopped.
  * `accuracy::Float64`: Estimate of the relative accuracy of the `solution`.
  * `accepted_steps::Int`: Number of steps that got accepted.
  * `rejected_steps::Int`: Number of steps that got rejected.
  * `extended_precision::Bool`: Indicate whether extended precision is necessary to achieve the accuracy of the `solution`.
  * `extended_precision_used::Bool`: This is `true` if during the tracking at any point extended precision was used.
