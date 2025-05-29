```
constraint_short_pipe_flow(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

短いパイプに沿った流量を流れの方向に基づいて制限する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`は流量が制限される短いパイプのインデックス、`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方の）方向に進むときの*最小*（正の）流量です。
