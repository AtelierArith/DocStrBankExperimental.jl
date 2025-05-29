```
solve!(solver, model; kwargs...)
solve!(solver, model, stats; kwargs...)
```

`solver`を`model`に適用します。

# 引数

  * `solver::AbstractOptimizationSolver`: 解決に必要なすべてのストレージを保持するソルバー構造
  * `model::AbstractNLPModel`: 解決されるモデル、`NLPModels.jl`を参照
  * `stats::GenericExecutionStats`: 解決情報を保持する統計構造。

最初の呼び出しは新しい`GenericExecutionStats`を割り当てて返します。2回目は事前に割り当てられた統計構造を埋め、効率的な再解決を可能にします。

`kwargs`はソルバーに渡されます。

# 戻り値

  * `stats::GenericExecutionStats`: 解決情報を保持する統計構造。
