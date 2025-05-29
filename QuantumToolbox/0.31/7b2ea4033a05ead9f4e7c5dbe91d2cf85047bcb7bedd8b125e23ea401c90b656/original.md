```
SteadyStateLinearSolver(alg = KrylovJL_GMRES(), Pl = nothing, Pr = nothing)
```

A solver which solves [`steadystate`](@ref) by finding the inverse of Liouvillian [`SuperOperator`](@ref) using the `alg`orithms given in [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/).

# Arguments

  * `alg::SciMLLinearSolveAlgorithm=KrylovJL_GMRES()`: algorithms given in [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/)
  * `Pl::Union{Function,Nothing}=nothing`: left preconditioner, see documentation [Solving for Steady-State Solutions](@ref doc:Solving-for-Steady-State-Solutions) for more details.
  * `Pr::Union{Function,Nothing}=nothing`: right preconditioner, see documentation [Solving for Steady-State Solutions](@ref doc:Solving-for-Steady-State-Solutions) for more details.
