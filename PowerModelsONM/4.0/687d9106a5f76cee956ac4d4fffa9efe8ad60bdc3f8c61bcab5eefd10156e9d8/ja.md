```
optimize_switches(
    subnetwork::Dict{String,<:Any},
    prob::Function,
    solver;
    formulation=PMD.LPUBFDiagPowerModel
)::Dict{String,Any}
```

単一のサブネットワーク（マルチネットワークではなく）での負荷シェディングのためにスイッチの状態を最適化します（`prob`を使用）。

オプションで、PowerModelsDistributionの`formulation`を独立して設定できますが、デフォルトではLinDist3Flowです。
