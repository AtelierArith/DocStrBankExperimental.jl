```
run!(sim::SimulationWorkspace, dt::Float64, t_end::Float64, step!::Function; kwargs...)
```

結果を時間的に進めてエクスポートするためのユーティリティ関数です。時間ステップ `dt`、最終時間 `t_end`、および関数 $step!(sim::SimulationWorkspace, time::Float64).$ を指定します。キーワード引数：

  * `nframes::Bool` (データを何回エクスポートすべきですか？)
  * `path::String` (データをどこにエクスポートしますか？)
  * `save_points::Bool` (ポイントデータをエクスポートすべきですか？)
  * `save_grid:::Bool` (グリッドデータをエクスポートすべきですか？)
  * `save_csv::Bool` (グローバル変数をcsvデータとしてエクスポートすべきですか？)
  * `vtp_vars` (どのローカル変数をエクスポートすべきですか？)
  * `csv_vars` (どのグローバル変数をエクスポートすべきですか？)
  * `postproc!::Function` (提供されている場合、データが保存される直前に `postproc!(sim, dt)` が呼び出されます。

出力ファイルに影響を与える（シミュレーション自体には影響を与えない）いくつかの（高コストの）後処理に使用してください。）

これは一定の時間ステップを前提としています。適応時間ステップの例については `examples/sedov.jl` を参照してください。
