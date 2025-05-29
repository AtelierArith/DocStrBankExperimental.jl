```julia
solve(prob::IntegralProblem, alg::SciMLBase.AbstractIntegralAlgorithm; kwargs...)
```

## キーワード引数

`solve`への引数は、すべての数値積分法で共通です。これらの共通引数は次のとおりです。

  * `maxiters`（最大反復回数）
  * `abstol`（目的値の変化に対する絶対許容誤差）
  * `reltol`（目的値の変化に対する相対許容誤差）
