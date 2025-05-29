```julia
struct Postprocess
```

シミュレーションに対する後処理オプションを含みます。`run_simulation(config, sim_params; postprocess = Postprocess(...))`が非空の`output_file`で呼び出されると、`HallThruster`はシミュレーション結果をJSONファイルに書き込みます。ファイル内の結果はフィールドに従って変換されます。

## フィールド

  * `output_file::String`: 出力が書き込まれるファイル。空の場合、出力は書き込まれません。
  * `average_start_time::Float64`: 平均化を開始する時間。ゼロ未満の場合、平均化された出力は書き込まれません。
  * `save_time_resolved::Bool`: 時間解像度の出力が保存されるかどうか。trueの場合、シミュレーションの各フレームが出力ファイルに書き込まれます。
