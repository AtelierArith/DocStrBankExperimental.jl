```
SteadyStateLinearSolver(alg = KrylovJL_GMRES(), Pl = nothing, Pr = nothing)
```

[`steadystate`](@ref) を解くソルバーで、`alg`orithms を使用して Liouvillian [`SuperOperator`](@ref) の逆を見つけます。これは [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/) に記載されています。

# 引数

  * `alg::SciMLLinearSolveAlgorithm=KrylovJL_GMRES()`: [`LinearSolve.jl`](https://docs.sciml.ai/LinearSolve/stable/) に記載されているアルゴリズム
  * `Pl::Union{Function,Nothing}=nothing`: 左の前処理器。詳細については、[定常状態解の解法](@ref doc:Solving-for-Steady-State-Solutions) のドキュメントを参照してください。
  * `Pr::Union{Function,Nothing}=nothing`: 右の前処理器。詳細については、[定常状態解の解法](@ref doc:Solving-for-Steady-State-Solutions) のドキュメントを参照してください。
