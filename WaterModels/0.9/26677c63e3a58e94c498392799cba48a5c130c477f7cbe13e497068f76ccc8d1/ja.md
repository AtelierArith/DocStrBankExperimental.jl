```
constraint_pipe_head(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
)
```

正の（前方）および負の（逆）流れ方向におけるヘッド損失（差）を制限する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`a`はパイプのインデックス、`node_fr`はパイプをモデル化する弧の尾部ノードのインデックス、`node_to`はパイプをモデル化する弧の頭部ノードのインデックスです。
