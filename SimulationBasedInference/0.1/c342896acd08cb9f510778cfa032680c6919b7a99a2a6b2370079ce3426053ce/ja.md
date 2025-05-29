```
init(::SimulatorInferenceProblem, ::EKS, ensemble_alg; kwargs...)
```

与えられた `SimulatorInferenceProblem` のために、アンサンブルカルマンサンプリングアルゴリズムを使用してEKSを初期化します。このメソッドは、与えられた推論問題と `named_data` ペアから `EnsembleKalmanProcess` を自動的に構築します。`initial_ens` が提供されていない場合、初期アンサンブルは事前分布からサンプリングされます。
