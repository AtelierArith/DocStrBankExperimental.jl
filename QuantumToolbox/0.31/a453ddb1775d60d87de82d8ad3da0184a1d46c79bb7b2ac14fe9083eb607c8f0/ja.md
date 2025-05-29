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

マスター方程式を使用した開放量子系の時間発展、ヒルベルト部分空間の次元を動的に変更します。

# 注意事項

  * `alg` に関する詳細は [`DifferentialEquations.jl` (ODE Solvers)](https://docs.sciml.ai/DiffEqDocs/stable/solvers/ode_solve/) を参照してください。
  * `kwargs` に関する詳細は [`DifferentialEquations.jl` (Keyword Arguments)](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/) を参照してください。
