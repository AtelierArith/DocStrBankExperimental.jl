```
constraint_on_off_des_pipe_head_loss(
    wm::AbstractLAModel,
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

設計パイプを通る摩擦ヘッドロスを、非線形で非凸なヘッドロス関係の区分線形近似を介してモデル化する制約を追加します。ここで、`wm`はWaterModelsオブジェクトです。`n`は考慮されるサブネットワーク（または時間）インデックスです。`a`は設計パイプのインデックスです。`node_fr`は設計パイプのテールノードのインデックスです。`node_to`は設計パイプのヘッドノードのインデックスです。`exponent`はヘッドロス関数における流量の指数です（すなわち、Hazen-Williamsヘッドロスの場合は1.852、Darcy-Weisbachヘッドロスの場合は2.0）。`L`は設計パイプの長さです。`r`は設計パイプの単位長さあたりの抵抗です。`q_max_reverse`は、流れが負の方向に進むときの*最大*（負の）流量です（これは負の方向に進むときの*最小*流量の大きさに対応します）。`q_min_forward`は、流れが正の（前方）方向に進むときの*最小*（正の）流量です。方向に基づく流量制限は、現在これらの制約では使用されていません。
