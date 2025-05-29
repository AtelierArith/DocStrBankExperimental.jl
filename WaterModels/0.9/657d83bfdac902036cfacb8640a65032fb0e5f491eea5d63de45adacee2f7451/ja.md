水モデル変数の境界を反復的に絞り込みます。デフォルトでは、関数は境界絞り込みを行うためにPWLRD緩和を使用します。

# 例

関数は次のように呼び出すことができます：

```
gurobi = JuMP.optimizer_with_attributes(Gurobi.Optimizer)
solve_obbt_owf!("examples/data/epanet/van_zyl.inp", gurobi)
```

# キーワード引数

  * `model_type`: 境界絞り込みを行うために使用する緩和。
  * `max_iter`: 実行する境界絞り込み反復の最大数。
  * `time_limit`: 境界絞り込みアルゴリズムの最大時間（秒）。
  * `upper_bound`: 問題のための局所的な実行可能解の目的を指定するために使用できます。
  * `upper_bound_constraint`: 各境界絞り込み解の探索空間を減少させるために追加の制約を加えるために使用できるブールオプション。このオプションは、上限を指定せずに`true`に設定することはできません。
  * `use_relaxed_network`: 境界絞り込みのために緩和されたスナップショット可能なバージョンの元のマルチネットワーク問題を使用するかどうかを指定するブールオプション。
