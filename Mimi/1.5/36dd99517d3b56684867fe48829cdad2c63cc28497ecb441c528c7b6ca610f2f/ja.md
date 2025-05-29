```
explore(sim_inst::SimulationInstance; title="Electron", model_index::Int = 1, scen_name::Union{Nothing, String} = nothing, results_output_dir::Union{Nothing, String} = nothing)
```

`SimulationInstance` `sim` の保存された変数の出力分布を探索するためのUIを生成します。モデル `model_index` とシナリオ名 `scen_name` の結果を、タイトル `title` のウィンドウで表示します。オプションの引数は、`model_index` が `1`、`scen_name` が `nothing`（シナリオ次元がないと仮定）で、タイトルが `Electron` のウィンドウをデフォルトとします。`results_output_dir` キーワード引数は、`run` に提供されたメイン出力ディレクトリを指し、すべてのサブディレクトリが保持されます。提供された場合、結果はそこに保存されていると仮定されます。そうでない場合、結果は `results.sim` に保持されていると仮定され、出力フォルダには保存されていないと見なされます。
