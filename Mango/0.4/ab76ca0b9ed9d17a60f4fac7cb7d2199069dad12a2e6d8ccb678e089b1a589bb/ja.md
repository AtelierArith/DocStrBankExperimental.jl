```
run_in_simulation(runnable::Function, agents::Agent, n_steps::Int; start_time::DateTime=DateTime(2000, 1, 1), step_size_s::Int=DISCRETE_EVENT)
```

エージェントをシミュレーションコンテナ内でシミュレーションとして実行します。

コンテナがアクティブな間に[`SimulationContainer`](@ref)内で`runnable`を実行します。`runnable`の後、シミュレーションコンテナは`step_size_s`（デフォルトは離散イベント）で`n_steps`回ステップされます。開始時間は`start_time`を使用して指定できます。
