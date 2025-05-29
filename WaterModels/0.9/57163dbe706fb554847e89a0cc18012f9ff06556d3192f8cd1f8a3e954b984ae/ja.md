```
constraint_des_pipe_flow(
    wm::AbstractNCDModel,
    n::Int,
    k::Int,
    node_fr::Int,
    node_to::Int,
    des_pipes::Array{Int,1}
)
```

設計パイプに沿った弧のすべての方向変数が互いに等しいことを保証する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`k`は各設計パイプの2つの共通ノードを接続する弧のインデックス、`node_fr`は各設計パイプをモデル化する弧の尾ノードのインデックス、`node_to`は各設計パイプをモデル化する弧の頭ノードのインデックス、`des_pipes`は同じ弧`k`に沿って存在する設計パイプのベクトルです。
