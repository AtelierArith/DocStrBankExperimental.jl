```
step_simulation(container::SimulationContainer, step_size_s::Real=DISCRETE_EVENT)::Union{SimulationResult,Nothing}
```

シミュレーションを連続時間スパンを使用して、または次のイベントが発生するまでステップします。

連続シミュレーションでは、`step_size_s`を自由に選択できますが、離散イベントタイプでは`step_size_s`にDISCRETE*EVENTを設定する必要があります。
