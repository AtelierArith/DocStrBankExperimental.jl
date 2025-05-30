```julia
CommonSolve.solve!(iter)
```

方程式または他の数学的問題を、引数で指定されたアルゴリズムを使用して解決します。一般的に、インターフェースは次のようになります。

```julia
iter = CommonSolve.init(prob::ProblemType,alg::SolverType; kwargs...)::IterType
CommonSolve.solve!(iter)::SolutionType
```

キーワード引数は、すべてのアルゴリズムの選択に対して一貫しています。`iter`タイプは、異なる問題タイプに対して異なります。
