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

量子系の時間発展をモンテカルロ波動関数法と動的シフトフォックアルゴリズムを用いて行います。

# 注意事項

  * `alg` の詳細については、[`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/)を参照してください。
  * `kwargs` の詳細については、[`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/)を参照してください。
