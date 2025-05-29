```
FiniteReservoirProblem(eq, rstop, tstop; i, b, capacity) <: AbstractFiniteProblem
```

Models `eq` in the domain `0 ≤ r ≤ rstop` with initial condition `i` and a reservoir boundary condition.

# Arguments

  * `eq`: equation to solve.
  * `rstop`: length of the domain.
  * `tstop=Inf`: final time. If `Inf`, the solution is computed until the steady state is reached.

# Keyword arguments

  * `i`: initial value.
  * `b`: boundary value.
  * `capacity`: reservoir capacity.
