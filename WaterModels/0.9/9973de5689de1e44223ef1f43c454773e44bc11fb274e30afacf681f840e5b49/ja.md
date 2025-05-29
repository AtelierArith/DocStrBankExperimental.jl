```
constraint_pipe_head_loss(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    exponent::Float64,
    L::Float64,
    r::Float64,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

パイプを通る摩擦ヘッド損失をモデル化する制約を追加します。ここで、`wm`はWaterModelsオブジェクトです。`n`は考慮されるサブネットワーク（または時間）インデックスです。`a`はパイプのインデックスです。`node_fr`はパイプのテールノードのインデックスです。`node_to`はパイプのヘッドノードのインデックスです。`exponent`はヘッド損失関数における流量の指数です（すなわち、Hazen-Williamsヘッド損失の場合は1.852、Darcy-Weisbachヘッド損失の場合は2.0）。`L`はパイプの長さです。`r`はパイプの単位長さあたりの抵抗です。`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量であり（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。
