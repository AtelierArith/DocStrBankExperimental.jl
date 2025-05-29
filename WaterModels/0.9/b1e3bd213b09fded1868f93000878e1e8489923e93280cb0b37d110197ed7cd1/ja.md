```
constraint_des_pipe_head(
    wm::AbstractNCDModel,
    n::Int,
    k::Int,
    node_fr::Int,
    node_to::Int,
    des_pipes::Array{Int,1}
)
```

設計パイプに沿った弧のヘッド差変数が、その単一の弧に沿った実際のヘッド差に合計されることを保証する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`k`は各設計パイプの2つの共通ノードを接続する弧のインデックス、`node_fr`は各設計パイプをモデル化する弧のテールノードのインデックス、`node_to`は各設計パイプをモデル化する弧のヘッドノードのインデックス、`des_pipes`は同じ弧`k`に存在する設計パイプのベクトルです。
