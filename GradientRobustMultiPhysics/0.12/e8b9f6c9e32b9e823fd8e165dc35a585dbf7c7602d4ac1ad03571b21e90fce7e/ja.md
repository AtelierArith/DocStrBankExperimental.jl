```
advance_until_stationarity!(TCS::TimeControlSolver, timestep; stationarity_threshold = 1e-11, maxtimesteps = 100, do_after_each_timestep = nothing)
```

与えられた（初期）タイムステップで時間を進め、定常状態が検出されるまで（変数の変化が閾値未満）または最大タイムステップ数を超えるまで、TimeControlSolverを進めます。関数do*after*timestepは各タイムステップの後に呼び出され、データの印刷/保存（および将来的なタイムステップ制御のために使用される可能性があります）に使用できます。
