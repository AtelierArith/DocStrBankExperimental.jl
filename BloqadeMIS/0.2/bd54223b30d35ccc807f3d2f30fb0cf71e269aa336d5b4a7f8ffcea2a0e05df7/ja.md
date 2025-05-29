```
independent_set_probabilities([f], reg::YaoAPI.AbstractRegister, graph_or_mis)
```

与えられた後処理関数 `f(config) -> config` を使用して独立集合の確率を計算します。デフォルトの後処理関数 `f` は、すべての構成を独立集合に減少させるだけです。

# 引数

  * `f`: オプションの後処理関数、デフォルトは [`to_independent_set`](@ref)。
  * `reg`: 必須、レジスタオブジェクト。
  * `graph_or_mis`: 問題グラフまたは問題グラフのMISサイズ（[`exact_solve_mis`](@ref) を介して計算できます）。
