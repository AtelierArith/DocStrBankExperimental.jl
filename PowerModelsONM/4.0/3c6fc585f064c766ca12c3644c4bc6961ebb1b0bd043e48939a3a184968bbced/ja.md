```
run_fault_study(
    subnetwork::Dict{String,<:Any},
    faults::Dict{String,<:Any},
    solver
)::Dict{String,Any}
```

`PowerModelsProtection.solve_mc_fault_study`を使用して、`faults`で定義された複数の障害を解決し、`subnetwork`に適用します。つまり、マルチネットワークではなく、非線形の`solver`を使用します。

`PowerModelsDistribution.IVRUPowerModel`の使用が必要です。
