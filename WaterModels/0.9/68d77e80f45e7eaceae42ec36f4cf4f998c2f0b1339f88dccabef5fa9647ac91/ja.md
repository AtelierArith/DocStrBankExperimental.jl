```
constraint_on_off_des_pipe_head_loss(
    wm::AbstractNCModel,
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

設計パイプを通過する摩擦ヘッド損失をモデル化する制約を追加します。ここで、`wm`はWaterModelsオブジェクトであり、`n`は考慮されるサブネットワーク（または時間）インデックスです。`a`は設計パイプのインデックスであり、`node_fr`は設計パイプのテールノードのインデックス、`node_to`は設計パイプのヘッドノードのインデックスです。`exponent`はヘッド損失関数における流量の指数（すなわち、Hazen-Williamsヘッド損失の場合は1.852、Darcy-Weisbachヘッド損失の場合は2.0）であり、`L`は設計パイプの長さ、`r`は設計パイプの単位長さあたりの抵抗、`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。ただし、`AbstractNCModel`タイプの場合、これらの方向に基づく流量制限は使用されません。設計パイプが構築されていない場合、流量は[`constraint_on_off_des_pipe_flow`](@ref)によってゼロに強制され、ここでのヘッド損失はヘッド損失方程式によってゼロに制約されます。
