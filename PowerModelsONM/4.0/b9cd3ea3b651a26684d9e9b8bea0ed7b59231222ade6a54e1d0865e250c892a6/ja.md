```
run_stability_analysis(
    subnetwork::Dict{String,<:Any},
    omega0::Real,
    rN::Int,
    solver;
    formulation::Type=PMD.ACPUPowerModel
)::Bool
```

単一のサブネットワーク（マルチネットワークではない）に対して非線形の `solver` を使用して安定性分析を実行します。
