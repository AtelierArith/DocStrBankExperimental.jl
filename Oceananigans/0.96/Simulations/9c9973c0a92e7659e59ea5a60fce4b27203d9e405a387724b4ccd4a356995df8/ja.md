```
Simulation(model; Δt,
           verbose = true,
           stop_iteration = Inf,
           stop_time = Inf,
           wall_time_limit = Inf,
           minimum_relative_step = 0)
```

`Δt`の時間ステップを持つ`model`のための`Simulation`を構築します。

# キーワード引数

  * `Δt`: シミュレーションの時間ステップを指定する必須のキーワード引数。定数時間ステップの場合は`Number`、適応時間ステッピングの場合は`TimeStepWizard`を指定できます。
  * `stop_iteration`: この回数のイテレーションの後にシミュレーションを停止します。
  * `stop_time`: この量のモデルクロック時間が経過したらシミュレーションを停止します。
  * `wall_time_limit`: この秒数の壁時計時間を超えてシミュレーションが実行されている場合、シミュレーションを停止します。
  * `minimum_relative_step`: `Δt * minimum_relative_step`より小さい時間ステップはスキップされます。これにより、圧力をディスクに書き込む際に非常に高い値を避けることができます。デフォルト値は0です。詳細についてはgithub.com/CliMA/Oceananigans.jl/issues/3593を参照してください。
