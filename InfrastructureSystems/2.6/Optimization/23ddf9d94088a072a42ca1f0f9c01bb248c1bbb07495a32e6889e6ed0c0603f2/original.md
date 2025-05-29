```julia
read_dual(
    res::InfrastructureSystems.Optimization.OptimizationProblemResults,
    args...;
    kwargs...
) -> DataFrames.DataFrame

```

Return the values for the requested dual key for a problem. Accepts a vector of keys for the return of the values.

# Arguments

  * `dual::Tuple{Type{<:ConstraintType}, Type{<:PSY.Component}` : Tuple with dual type and device type for the desired results
  * `start_time::Dates.DateTime` : initial time of the requested results
  * `len::Int`: length of results
