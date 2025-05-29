```
constraint_des_pipe_flow(
    wm::AbstractWaterModel,
    k::Int,
    node_fr::Int,
    node_to::Int;
    nw::Int=nw_id_default,
    kwargs...,
)
```

アークに沿った設計パイプのフロー変数が同じ方向を向くことを保証する制約を追加するための制約テンプレートです。ここで、`wm`はWaterModelsオブジェクト、`k`は各設計パイプの2つの共通ノードを接続するアークのインデックス、`node_fr`は各設計パイプをモデル化するアークのテールノードのインデックス、`node_to`は各設計パイプをモデル化するアークのヘッドノードのインデックス、`nw`はマルチネットワーク内のサブネットワークのインデックス、`des_pipes`は同じアーク`k`に沿って存在する設計パイプのインデックスのベクトルです。
