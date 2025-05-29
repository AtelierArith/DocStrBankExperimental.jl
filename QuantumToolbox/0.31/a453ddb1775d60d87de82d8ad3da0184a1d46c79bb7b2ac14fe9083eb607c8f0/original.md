```
dfd_mesolve(H::Function, ψ0::QuantumObject,
    tlist::AbstractVector, c_ops::Function, maxdims::AbstractVector,
    dfd_params::NamedTuple=NamedTuple();
    alg::OrdinaryDiffEqAlgorithm=Tsit5(),
    e_ops::Function=(dim_list) -> Vector{Vector{T1}}([]),
    params::NamedTuple=NamedTuple(),
    tol_list::Vector{<:Number}=fill(1e-8, length(maxdims)),
    kwargs...)
```

Time evolution of an open quantum system using master equation, dynamically changing the dimension of the Hilbert subspaces.

# Notes

  * For more details about `alg` please refer to [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)
