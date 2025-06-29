```
constraint_on_off_des_pipe_flow(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

設計パイプの建設状況に基づいて、設計パイプに沿った流量の量を制限する制約を追加します（すなわち、パイプが建設されている場合は流量が制限されず、パイプが建設されていない場合は流量がゼロになります）。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`は設計パイプのインデックス、`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。ただし、`AbstractNCModel`タイプの場合、これらの方向に基づく流量制限は使用されません。
