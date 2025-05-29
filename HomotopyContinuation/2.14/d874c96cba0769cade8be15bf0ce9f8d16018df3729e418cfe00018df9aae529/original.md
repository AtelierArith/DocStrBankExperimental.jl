```
solver_startsolutions(args...; kwargs...)
```

Takes the same input as [`solve`](@ref) but instead of directly solving the problem returns a [`Solver`](@ref) struct and the start solutions.

## Example

Calling `solve(args..; kwargs...)` is equivalent to

```julia
solver, starts = solver_startsolutions(args...; kwargs...)
solve(solver, starts)
```
