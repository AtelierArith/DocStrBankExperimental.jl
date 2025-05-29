```
sol = solve(s::AbstractSimulator, x0, tspan,  args...; kwargs...)
```

Simulate the system represented by `s` from initial state `x0` over time span `tspan = (t0,tf)`. `args` and `kwargs` are sent to the `solve` function from `OrdinaryDiffEq`, e.g., `solve(s, x0, tspan,  Tsit5(), reltol=1e-5)` solves the problem with solver [`Tsit5()`](http://docs.juliadiffeq.org/stable/solvers/ode_solve.html) and relative tolerance 1e-5.

See also `Simulator` `lsim`
