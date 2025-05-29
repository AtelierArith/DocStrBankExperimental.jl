```
constraint_on_off_regulator_flow(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    q_min_forward::Float64
)
```

レギュレーターの動作状況に基づいて、レギュレーターを通過する流量の量を制限する制約を追加します（すなわち、レギュレーターがアクティブな場合は流量が制限され、そうでない場合は流量がゼロになります）。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はレギュレーターのインデックス、`q_min_forward`はレギュレーターがアクティブなときの*最小*（正の）流量です。
