```
struct SolverIterator{T <: Real}
SolverIterator(solver, times)
```

Given a solver and a vector of times,  this iterator will return the state of the solver at each time.

The solver will be mutated to hold the solution from the last time given.

# Examples

```julia
julia> solver = DP5Solver(fcn, 0.0, [0.0])

julia> times = [1.0, 2.0, 3.0]

julia> intermediate_vals = []

julia> for (time, value) in SolverIterator(solver, times)
            push!(intermediate_values, value[])
        end

```
