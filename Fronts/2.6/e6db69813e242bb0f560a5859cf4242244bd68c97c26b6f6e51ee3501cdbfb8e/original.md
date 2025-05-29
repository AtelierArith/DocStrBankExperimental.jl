```
FiniteDirichletProblem(eq, rstop[, tstop]; i, b) <: AbstractFiniteProblem
```

Models `eq` in the domain `0 ≤ r ≤ rstop` with initial condition `i` and boundary condition `b`.

# Arguments

  * `eq`: equation to solve.
  * `rstop`: length of the domain.
  * `tstop=Inf`: final time. If `Inf`, the solution is computed until the steady state is reached.

# Keyword arguments

  * `i`: initial value.
  * `b`: boundary value.
