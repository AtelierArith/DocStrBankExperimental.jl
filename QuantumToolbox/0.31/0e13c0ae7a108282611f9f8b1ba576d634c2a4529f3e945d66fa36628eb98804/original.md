```
SteadyStateODESolver(
    alg = Tsit5(),
    ψ0 = nothing,
    tmax = Inf,
    )
```

An ordinary differential equation (ODE) solver for solving [`steadystate`](@ref).

Solve the stationary state based on time evolution (ordinary differential equations; `OrdinaryDiffEq.jl`) with a given initial state.

The termination condition of the stationary state $|\rho\rangle\rangle$ is that either the following condition is `true`:

$$
\lVert\frac{\partial |\hat{\rho}\rangle\rangle}{\partial t}\rVert \leq \textrm{reltol} \times\lVert\frac{\partial |\hat{\rho}\rangle\rangle}{\partial t}+|\hat{\rho}\rangle\rangle\rVert
$$

or

$$
\lVert\frac{\partial |\hat{\rho}\rangle\rangle}{\partial t}\rVert \leq \textrm{abstol}
$$

# Arguments

  * `alg::OrdinaryDiffEqAlgorithm=Tsit5()`: The algorithm to solve the ODE.
  * `ψ0::Union{Nothing,QuantumObject}=nothing`: The initial state of the system. If not specified, a random pure state will be generated.
  * `tmax::Real=Inf`: The final time step for the steady state problem.

For more details about the solvers, please refer to [`OrdinaryDiffEq.jl`](https://docs.sciml.ai/OrdinaryDiffEq/stable/).
