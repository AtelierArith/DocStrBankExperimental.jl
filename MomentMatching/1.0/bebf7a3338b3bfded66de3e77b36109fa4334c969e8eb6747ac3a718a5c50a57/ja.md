```julia
struct NumParMM{S<:AbstractFloat, T<:Integer}
```

# 説明

推定手順のための数値パラメータを格納する構造体。

# フィールド

  * `sobolinds`: 使用するSobol点のインデックス
  * `Nloc`: 推定のローカルステージで評価する最良点の数（またはグローバルステージのみの場合は保存するため、[`matchmom`](@ref)を参照）
  * `full_lb_global`: グローバルステージにおけるパラメータの下限
  * `full_ub_global`: グローバルステージにおけるパラメータの上限
  * `onlyglo`: 論理値、グローバル最適化のみが実行される場合はtrue
  * `onlyloc`: 論理値、ローカル最適化のみが実行される場合はtrue
  * `local_opt_settings`: ローカルステージで使用される最適化の設定
