```
PiccoloOptions
```

Piccolo量子最適制御ライブラリのオプション。

# フィールド

  * `verbose::Bool = true`: 詳細な出力を表示
  * `timesteps_all_equal::Bool = true`: 等しいタイムステップを使用
  * `rollout_integrator::Function = expv`: ロールアウトに使用する積分器
  * `geodesic = true`: 最適化を初期化するために測地線を使用。
  * `zero_initial_and_final_derivative::Bool=false`: 初期および最終制御パルスの導関数をゼロにする。
  * `complex_control_norm_constraint_name::Union{Nothing, Symbol} = nothing`: 複素制御ノルム制約の名前。
  * `complex_control_norm_constraint_radius::Float64 = 1.0`: 複素制御ノルム制約の半径。
  * `bound_state::Bool = false`: 状態を制約する。
  * `leakage_suppression::Bool = false`: 漏れを抑制する。
  * `R_leakage::Float64 = 1.0`: 漏れ抑制パラメータ。
