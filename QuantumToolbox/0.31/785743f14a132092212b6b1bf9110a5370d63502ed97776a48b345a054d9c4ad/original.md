```
dsf_mcsolve(H::Function,
    ψ0::QuantumObject,
    tlist::AbstractVector, c_ops::Function,
    op_list::Vector{TOl},
    α0_l::Vector{<:Number}=zeros(length(op_list)),
    dsf_params::NamedTuple=NamedTuple();
    alg::OrdinaryDiffEqAlgorithm=Tsit5(),
    e_ops::Function=(op_list,p) -> Vector{TOl}([]),
    params::NamedTuple=NamedTuple(),
    δα_list::Vector{<:Real}=fill(0.2, length(op_list)),
    ntraj::Int=500,
    ensemblealg::EnsembleAlgorithm=EnsembleThreads(),
    jump_callback::LindbladJumpCallbackType=ContinuousLindbladJumpCallback(),
    krylov_dim::Int=max(6, min(10, cld(length(ket2dm(ψ0).data), 4))),
    progress_bar::Union{Bool,Val} = Val(true)
    kwargs...)
```

Time evolution of a quantum system using the Monte Carlo wave function method and the Dynamical Shifted Fock algorithm.

# Notes

  * For more details about `alg` please refer to [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)
  * For more details about `kwargs` please refer to [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)
