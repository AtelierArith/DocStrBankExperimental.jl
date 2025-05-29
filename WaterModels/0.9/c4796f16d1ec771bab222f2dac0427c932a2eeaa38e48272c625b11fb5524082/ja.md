```
constraint_pipe_head_loss(
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

パイプを通る摩擦によるヘッドロスを、非線形で非凸なヘッドロス関係の区分線形近似を介してモデル化する制約を追加します。ここで、`wm`はWaterModelsオブジェクトであり、`n`は考慮されるサブネットワーク（または時間）インデックスです。`a`はパイプのインデックスであり、`node_fr`はパイプの尾部ノードのインデックス、`node_to`はパイプの頭部ノードのインデックスです。`exponent`はヘッドロス関数における流量の指数（すなわち、Hazen-Williamsヘッドロスの場合は1.852、Darcy-Weisbachヘッドロスの場合は2.0）であり、`L`はパイプの長さ、`r`はパイプの単位長さあたりの抵抗です。`q_max_reverse`は流れが負の方向に進むときの*最大*（負の）流量であり（これは負の方向に進むときの*最小*流量の大きさに対応します）、`q_min_forward`は流れが正の（前方）方向に進むときの*最小*（正の）流量です。`q_max_reverse`と`q_min_forward`は、この定式化では使用されていないことに注意してください。なぜなら、これは方向に基づいていないからです。
