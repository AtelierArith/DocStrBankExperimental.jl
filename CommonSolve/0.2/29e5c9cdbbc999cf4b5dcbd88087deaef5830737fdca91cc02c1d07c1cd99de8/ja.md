```julia
iter = CommonSolve.init(args...; kwargs...)
```

方程式またはその他の数学的問題を、引数で指定されたアルゴリズムを使用して解決します。一般的に、インターフェースは次のようになります。

```julia
iter = CommonSolve.init(prob::ProblemType,alg::SolverType; kwargs...)::IterType
CommonSolve.solve!(iter)::SolutionType
```

キーワード引数は、すべてのアルゴリズムの選択に対して一貫しています。`iter` 型は、異なる問題タイプに対して異なります。
