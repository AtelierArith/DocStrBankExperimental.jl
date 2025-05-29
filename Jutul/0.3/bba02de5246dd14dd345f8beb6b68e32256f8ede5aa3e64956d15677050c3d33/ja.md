```
HelperSimulator(model::M, T = Float64; state0 = setup_state(model), executor::E = Jutul.default_executor()) where {M, E}
```

指定された型 T の残差および/または蓄積項を計算するために使用できるヘルパーシミュレーターを構築します。Jutul を他のソルバーや自動微分のタイプに結合するのに便利です。
