```
dsf_mesolve(H::Function,
    ψ0::QuantumObject,
    tlist::AbstractVector, c_ops::Function,
    op_list::Vector{TOl},
    α0_l::Vector{<:Number}=zeros(length(op_list)),
    dsf_params::NamedTuple=NamedTuple();
    alg::OrdinaryDiffEqAlgorithm=Tsit5(),
    e_ops::Function=(op_list,p) -> Vector{TOl}([]),
    params::NamedTuple=NamedTuple(),
    δα_list::Vector{<:Number}=fill(0.2, length(op_list)),
    krylov_dim::Int=max(6, min(10, cld(length(ket2dm(ψ0).data), 4))),
    kwargs...)
```

マスター方程式と動的シフトフォックアルゴリズムを使用した開放量子系の時間発展。

# 注意事項

  * `alg` に関する詳細は、[`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/) を参照してください。
  * `kwargs` に関する詳細は、[`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) を参照してください。
