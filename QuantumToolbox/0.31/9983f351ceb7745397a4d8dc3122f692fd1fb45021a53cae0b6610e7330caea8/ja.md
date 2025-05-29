```
steadystate(
    H::QuantumObject{OpType},
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    solver::SteadyStateSolver = SteadyStateDirectSolver(),
    kwargs...,
)
```

異なるソルバーに基づいて定常状態を解きます。

# パラメータ

  * `H`: システムのハミルトニアンまたはリウビリアン。
  * `c_ops`: 崩壊演算子のリスト。
  * `solver`: 異なるソルバーについては、ドキュメント [Solving for Steady-State Solutions](@ref doc:Solving-for-Steady-State-Solutions) を参照してください。
  * `kwargs`: ソルバーのためのキーワード引数。
