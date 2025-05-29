```
steadystate(M::AbstractHEOMLSMatrix, ρ0, tspan; solver, verbose, SOLVEROptions...)
```

Solve the steady state of the auxiliary density operators based on time evolution (`OrdinaryDiffEq.jl`) with initial state is given in the type of density-matrix (`ρ0`).

# Parameters

  * `M::AbstractHEOMLSMatrix` : the matrix given from HEOM model, where the parity should be `EVEN`.
  * `ρ0::Union{QuantumObject,ADOs}` : system initial state (density matrix) or initial auxiliary density operators (`ADOs`)
  * `tspan::Number` : the time limit to find stationary state. Default to `Inf`
  * `solver::OrdinaryDiffEqAlgorithm` : The ODE solvers in package `DifferentialEquations.jl`. Default to `DP5()`.
  * `verbose::Bool` : To display verbose output and progress bar during the process or not. Defaults to `true`.
  * `SOLVEROptions` : extra options for solver

# Notes

  * For more details about `solver` please refer to [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * For more details about `SOLVEROptions` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)

# Returns

  * `::ADOs` : The steady state of auxiliary density operators.
