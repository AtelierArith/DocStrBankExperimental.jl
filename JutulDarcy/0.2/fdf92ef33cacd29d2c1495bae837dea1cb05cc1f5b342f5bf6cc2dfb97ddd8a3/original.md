```
coarsen_reservoir_case(case, coarsedim; kwargs...)
```

Coarsens the given reservoir case to the specified dimensions.

# Arguments

  * `case`: The reservoir case to be coarsened.
  * `coarsedim`: The target dimensions for the coarsened reservoir.

# Keyword Arguments

  * `method`: The method to use for partitioning. Defaults to `missing`.
  * `partitioner_arg`: A named tuple of arguments to be passed to the partitioner.
  * `setup_arg`: A named tuple of arguments to be passed to `coarsen_reservoir_model`.
  * `state_arg`: A named tuple of arguments to be passed to the state coarsening function.

# Returns

  * A coarsened version of the reservoir case.
