```
integrate!(solver, time)
```

Integrate the ODE problem that is part of solver to the end time `time`. `solver` can be a `DP5Solver` or a `DP8Solver` type.

The `solver` is mutated to hold the solution and `solver` state at the time `time`, allowing for  efficient integration to future end times of interest through subsequent calls to `integrate!` with  later times.

# Examples

```julia
julia> function fcn(x, y, f)
            f[1] = 0.85y[1]
        end

julia> solver = DP5Solver(fcn, 0.0, [19.0])

# Integrate from initial time of 0.0 to 1.0
julia> integrate!(solver, 1.0)

# integrate from the last time of 1.0 to 2.0
julia> integrate!(solver, 2.0)

# Solver object now holds solution and state at 2.0
julia> get_current_state(solver)
```
