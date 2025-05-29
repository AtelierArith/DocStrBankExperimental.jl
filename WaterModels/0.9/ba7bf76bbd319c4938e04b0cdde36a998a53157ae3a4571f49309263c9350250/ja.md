```
constraint_on_off_des_pipe_head_loss(
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

設計パイプを介した摩擦ヘッド損失をモデル化する制約を追加します。これは、非線形で非凸なヘッド損失関係の外部および区分線形内部近似を通じて行われます。ここで、`wm`はWaterModelsオブジェクトであり、`n`は考慮されるサブネットワーク（または時間）インデックスです。`a`は設計パイプのインデックスであり、`node_fr`は設計パイプのテールノードのインデックスです。`node_to`は設計パイプのヘッドノードのインデックスです。`exponent`はヘッド損失関数における流量の指数（すなわち、Hazen-Williamsヘッド損失の場合は1.852、Darcy-Weisbachヘッド損失の場合は2.0）です。`L`は設計パイプの長さであり、`r`は設計パイプの単位長さあたりの抵抗です。`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量であり（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。
