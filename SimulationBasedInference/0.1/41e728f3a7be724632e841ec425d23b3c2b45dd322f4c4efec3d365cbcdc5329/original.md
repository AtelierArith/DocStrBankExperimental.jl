```
init(forward_prob::SimulatorForwardProblem{<:AbstractODEProblem}, ode_alg; p=forward_prob.prob.p, saveat=[], solve_kwargs...)
```

Initializes a `SimulatorODEForwardSolver` for the given forward problem and ODE integrator algorithm. Additional keyword arguments are passed through to the integrator `init` implementation.
