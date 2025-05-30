```julia
CommonSolve.solve(args...; kwargs...)
```

方程式またはその他の数学的問題を、引数で指定されたアルゴリズムを使用して解決します。一般的に、インターフェースは次のようになります：

```julia
CommonSolve.solve(prob::ProblemType,alg::SolverType; kwargs...)::SolutionType
```

ここで、キーワード引数はすべてのアルゴリズムの選択に対して一貫しています。

デフォルトでは、`solve`はイテレータ形式で`solve!`を使用するように設定されています。すなわち：

```julia
solve(args...; kwargs...) = solve!(init(args...; kwargs...))
```
