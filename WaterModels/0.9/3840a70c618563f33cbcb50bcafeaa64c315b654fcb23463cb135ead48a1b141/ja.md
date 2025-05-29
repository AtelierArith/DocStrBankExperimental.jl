```
constraint_on_off_des_pipe_head_loss(
    wm::AbstractLRDModel,
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

設計パイプを通る摩擦ヘッドロスを、非線形で非凸なヘッドロス関係の線形外近似を介してモデル化する制約を追加します。ここで、`wm`はWaterModelsオブジェクトであり、`n`は考慮されるサブネットワーク（または時間）インデックスです。`a`は設計パイプのインデックスであり、`node_fr`は設計パイプのテールノードのインデックス、`node_to`は設計パイプのヘッドノードのインデックスです。`exponent`はヘッドロス関数における流量の指数（すなわち、Hazen-Williamsヘッドロスの場合は1.852、Darcy-Weisbachヘッドロスの場合は2.0）であり、`L`は設計パイプの長さ、`r`は設計パイプの単位長さあたりの抵抗、`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。
