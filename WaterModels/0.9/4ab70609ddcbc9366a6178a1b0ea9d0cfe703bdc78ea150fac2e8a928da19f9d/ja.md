```
constraint_des_pipe_head(
    wm::AbstractWaterModel,
    k::Int,
    node_fr::Int,
    node_to::Int;
    nw::Int=nw_id_default,
    kwargs...,
)
```

設計パイプに沿った弧の頭の差変数が、その弧に沿った実際の頭の差に合計されることを保証する制約を追加するための制約テンプレートです。ここで、`wm`はWaterModelsオブジェクト、`k`は各設計パイプの2つの共通ノードを接続する弧のインデックス、`node_fr`は各設計パイプをモデル化する弧の尾ノードのインデックス、`node_to`は各設計パイプをモデル化する弧の頭ノードのインデックス、`nw`はマルチネットワーク内のサブネットワークのインデックス、`des_pipes`は同じ弧`k`に沿って存在する設計パイプのインデックスのベクトルです。
