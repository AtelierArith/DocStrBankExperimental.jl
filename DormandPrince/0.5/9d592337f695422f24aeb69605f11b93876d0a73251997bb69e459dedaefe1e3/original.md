```
integrate!(callback, solver, times)
```

Integrate the ODE problem that is part of `solver` to the end times `times` and apply the callback on  the time and solution at each time.  `solver` can be a `DP5Solver` or a `DP8Solver` type.

At the end of all the times the solver holds the solution and solver state at the last time in `times`.

# Examples

```julia
julia> function fcn(x, y, f)
            f[1] = 0.85y[1]
        end

julia> times = [1.0, 1.1, 1.9, 2.4]

julia> solver = DP5Solver(fcn, 0.0, [19.0])

julia> intermediate_values = []

julia> integrate!(solver, times) do time, val
            push!(intermediate_values, val[])
        end
```
