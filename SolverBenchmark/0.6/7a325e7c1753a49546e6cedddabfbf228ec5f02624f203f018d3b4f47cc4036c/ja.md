```
bmark_solvers(solvers :: Dict{Symbol,Any}, args...; kwargs...)
```

一連の問題に対して一連のソルバーを実行します。

#### 引数

  * `solvers`: 各問題に渡されるソルバーの辞書
  * `solve_problems` によって受け入れられる他の位置引数、ソルバー名を除く

#### キーワード引数

`solve_problems` によって受け入れられる任意のキーワード引数

#### 戻り値

統計の `Dict{Symbol, AbstractExecutionStats}`。
