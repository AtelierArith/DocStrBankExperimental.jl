```julia
mutable struct SimParams{C<:HallThruster.CurrentController}
```

  * `grid::HallThruster.GridSpec`: グリッド指定子で、`HallThruster.EvenGrid(n)` または `HallThruster.UnevenGrid(n)` のいずれかで、nは希望するセルの数です。詳細については [Grid generation](@ref) を参照してください。
  * `dt::Float64`: シミュレーションの基本タイムステップ（秒単位）。詳細については [Timestepping](@ref) を参照してください。
  * `duration::Float64`: シミュレーションの期間（秒単位）。
  * `num_save::Int64`: `Solution` 構造体に保存するシミュレーションフレームの数。**デフォルト:** 1000
  * `verbose::Bool`: シミュレーションの実行時間などの情報がコンソールに出力されるかどうか。**デフォルト:** `true`
  * `print_errors::Bool`: エラーが `Solution` 構造体にキャプチャされるだけでなく、コンソールにも出力されるかどうか。**デフォルト:** `true`
  * `adaptive::Bool`: 適応的タイムステッピングを使用するかどうか。詳細については [Timestepping](@ref) を参照してください。**デフォルト:** `true`
  * `CFL::Float64`: 適応的タイムステッピングで使用されるCFL数。最大は0.799です。**デフォルト:** 0.799
  * `min_dt::Float64`: 適応的タイムステッピングで許可される最小タイムステップ（秒単位）。**デフォルト:** 1e-10
  * `max_dt::Float64`: 適応的タイムステッピングで許可される最大タイムステップ（秒単位）。**デフォルト:** 1e-7
  * `max_small_steps::Int64`: 適応的タイムステッピングで許可される最小サイズのタイムステップの最大数。**デフォルト:** 100
  * `current_control::HallThruster.CurrentController`: 放電電流コントローラー。**デフォルト:** `HallThruster.NoController()`
