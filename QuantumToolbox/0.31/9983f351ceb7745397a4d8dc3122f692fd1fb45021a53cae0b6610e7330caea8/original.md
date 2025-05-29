```
steadystate(
    H::QuantumObject{OpType},
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    solver::SteadyStateSolver = SteadyStateDirectSolver(),
    kwargs...,
)
```

Solve the stationary state based on different solvers.

# Parameters

  * `H`: The Hamiltonian or the Liouvillian of the system.
  * `c_ops`: The list of the collapse operators.
  * `solver`: see documentation [Solving for Steady-State Solutions](@ref doc:Solving-for-Steady-State-Solutions) for different solvers.
  * `kwargs`: The keyword arguments for the solver.
