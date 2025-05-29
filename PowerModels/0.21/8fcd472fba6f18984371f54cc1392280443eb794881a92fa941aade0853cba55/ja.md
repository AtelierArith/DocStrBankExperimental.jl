電圧の大きさと位相角の差の変数に対して、反復的に境界を厳密化します。

この関数は、これらの変数を明示的に持つ任意の凸緩和に対して呼び出すことができます。デフォルトでは、境界の厳密化を行うためにQC緩和を使用します。興味のある読者は、「電力ネットワーク最適化のための境界厳密化による凸緩和の強化」という論文を参照してください。

# 例

関数は次のように呼び出すことができます：

```
data, stats = solve_obbt_opf!("matpower/case3.m", Ipopt.Optimizer)
```

`data` には、厳密化された境界を持つ解析されたネットワークデータが含まれています。`stats` には、境界厳密化アルゴリズムからの情報出力が含まれています。おおよそ次のようになります：

```
Dict{String,Any} with 19 entries:
  "initial_relaxation_objective" => 5817.91
  "vm_range_init"                => 0.6
  "final_relaxation_objective"   => 5901.96
  "avg_vm_range_init"            => 0.2
  "final_rel_gap_from_ub"        => NaN
  "run_time"                     => 0.832232
  "model_type"            => AbstractPowerModel
  "avg_td_range_final"           => 0.436166
  "initial_rel_gap_from_ub"      => Inf
  "sim_parallel_run_time"        => 1.13342
  "upper_bound"                  => Inf
  "vm_range_final"               => 0.6
  "vad_sign_determined"          => 2
  "avg_td_range_init"            => 1.0472
  "avg_vm_range_final"           => 0.2
  "iteration_count"              => 5
  "td_range_init"                => 3.14159
  "td_range_final"               => 1.3085
```

# キーワード引数

  * `model_type`: 境界厳密化を行うために使用する緩和。現在、電圧の大きさと位相角の差の変数を明示的に持つ任意の緩和をサポートしています。
  * `max_iter`: 実行する境界厳密化の最大反復回数。
  * `time_limit`: 境界厳密化アルゴリズムの最大時間（秒）。
  * `upper_bound`: AC最適潮流問題のための局所的な実行可能解の目的を指定するために使用できます。
  * `upper_bound_constraint`: 各境界厳密化の解の探索空間を減少させるために追加の制約を加えるために使用できるブールオプション。このオプションは、上限を指定せずに `true` に設定することはできません。
  * `rel_gap_tol`: 緩和の目的値が `upper_bound` キーワードを使用して指定された上限に近いときにアルゴリズムを終了するために使用される許容誤差。
  * `min_bound_width`: 境界厳密化が行われない範囲。
  * `termination`: 平均または最大の境界改善の改善が `improvement_tol` よりも小さい場合、境界厳密化アルゴリズムは終了します。これは `termination = :avg` または `termination = :max` オプションを使用して指定されます。
  * `precision`: 厳密化された境界を丸める小数点以下の桁数。
