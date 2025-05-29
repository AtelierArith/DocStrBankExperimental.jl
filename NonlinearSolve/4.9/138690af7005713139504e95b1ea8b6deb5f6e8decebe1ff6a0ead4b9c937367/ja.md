```
NLSolversJL(method; autodiff = nothing)
NLSolversJL(; method, autodiff = nothing)
```

NLSolvers.jl 非線形方程式ソルバーのラッパーです。ヤコビ行列関数を自動的に構築し、ソルバーに供給します。

### 引数

  * `method`: 非線形システムを解くためのメソッドの選択。詳細については NLSolvers.jl のドキュメントを参照してください。
  * `autodiff`: ヤコビ行列を生成するためのメソッドの選択。デフォルトは `nothing` で、これは問題の仕様に応じてデフォルトが選択されることを意味します。これは、NonlinearSolve.jl でサポートされているバックエンドに依存する任意の有効な ADTypes.jl 自動微分タイプである可能性があります。
