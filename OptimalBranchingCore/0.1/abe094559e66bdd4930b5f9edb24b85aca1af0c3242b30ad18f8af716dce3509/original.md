```
branch_and_reduce(problem::AbstractProblem, config::BranchingStrategy; reducer::AbstractReducer=NoReducer(), result_type=Int, show_progress=false)
```

Branch the given problem using the specified solver configuration.

### Arguments

  * `problem`: The problem instance to solve.
  * `config`: The configuration for the solver, which is a [`BranchingStrategy`](@ref) instance.

### Keyword Arguments

  * `reducer::AbstractReducer=NoReducer()`: The reducer to reduce the problem size.
  * `result_type::Type{TR}`: The type of the result that the solver will produce.

### Returns

The resulting value, which may have different type depending on the `result_type`.
