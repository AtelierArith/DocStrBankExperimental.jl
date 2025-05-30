```julia
init(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## キーワード引数

`init`への引数は`solve`への引数と同じで、すべての最適化アルゴリズムで共通です。これらの共通引数は次のとおりです：

  * `maxiters`（最大反復回数）
  * `maxtime`（最適化が実行される最大時間）
  * `abstol`（目的値の変化に対する絶対許容誤差）
  * `reltol`（目的値の変化に対する相対許容誤差）
  * `callback`（コールバック関数）

一部の最適化アルゴリズムには、ドキュメントのソルバー部分およびそれぞれのドキュメントに記載された特別なキーワード引数があります。これらの引数は`kwargs...`として`init`に渡すことができます。

[`solve(prob::OptimizationProblem, alg, args...; kwargs...)`](@ref)も参照してください。
