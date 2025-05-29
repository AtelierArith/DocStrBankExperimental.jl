```
getTime(solution::FMUSolution)
```

Returns the Solution time.

# Arguments

  * `solution::FMUSolution`: Struct contains information about the solution `value`, `success`, `state` and  `events` of a specific FMU.

# Return

  * `solution.states.t::tType`: `solution.state` is a struct `ODESolution` with attribute t. `t` is the time points corresponding to the saved values of the ODE solution.
  * `solution.values.t::tType`: `solution.value` is a struct `ODESolution` with attribute t.`t` the time points corresponding to the saved values of the ODE solution.
  * If no solution time is  found `nothing` is returned.

#Source

  * using OrdinaryDiffEq: [ODESolution](https://github.com/SciML/SciMLBase.jl/blob/b10025c579bcdecb94b659aa3723fdd023096197/src/solutions/ode_solutions.jl)  (SciML/SciMLBase.jl)
  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
