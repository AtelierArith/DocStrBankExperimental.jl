```
SteadyStateODESolver(
    alg = Tsit5(),
    ψ0 = nothing,
    tmax = Inf,
    )
```

[`steadystate`](@ref)を解くための常微分方程式（ODE）ソルバーです。

与えられた初期状態に基づいて時間発展（常微分方程式; `OrdinaryDiffEq.jl`）に基づいて定常状態を解きます。

定常状態 $|\rho\rangle\rangle$ の終了条件は、次の条件のいずれかが `true` であることです：

$$
\lVert\frac{\partial |\hat{\rho}\rangle\rangle}{\partial t}\rVert \leq \textrm{reltol} \times\lVert\frac{\partial |\hat{\rho}\rangle\rangle}{\partial t}+|\hat{\rho}\rangle\rangle\rVert
$$

または

$$
\lVert\frac{\partial |\hat{\rho}\rangle\rangle}{\partial t}\rVert \leq \textrm{abstol}
$$

# 引数

  * `alg::OrdinaryDiffEqAlgorithm=Tsit5()`: ODEを解くためのアルゴリズム。
  * `ψ0::Union{Nothing,QuantumObject}=nothing`: システムの初期状態。指定されていない場合は、ランダムな純粋状態が生成されます。
  * `tmax::Real=Inf`: 定常状態問題の最終時間ステップ。

ソルバーの詳細については、[`OrdinaryDiffEq.jl`](https://docs.sciml.ai/OrdinaryDiffEq/stable/)を参照してください。
