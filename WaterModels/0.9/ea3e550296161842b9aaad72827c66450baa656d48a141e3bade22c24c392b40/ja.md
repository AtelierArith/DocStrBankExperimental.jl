```
constraint_pipe_head_loss(
    wm::AbstractPWLRDModel,
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

パイプを通る摩擦ヘッドロスをモデル化する制約を追加します。これは、非線形で非凸なヘッドロス関係の外部および区分線形内部近似を介して行われます。ここで、`wm`はWaterModelsオブジェクトであり、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はパイプのインデックス、`node_fr`はパイプの尾ノードのインデックス、`node_to`はパイプの頭ノードのインデックス、`exponent`はヘッドロス関数における流量の指数（すなわち、Hazen-Williamsヘッドロスの場合は1.852、Darcy-Weisbachヘッドロスの場合は2.0）、`L`はパイプの長さ、`r`はパイプの単位長さあたりの抵抗、`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。
