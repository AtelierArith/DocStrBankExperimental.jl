```
constraint_des_pipe_flow(
    wm::AbstractNCModel,
    n::Int,
    k::Int,
    node_fr::Int,
    node_to::Int,
    des_pipes::Array{Int,1}
)
```

現在、`AbstractNCModel`タイプのモデルに対しては何も行いません。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`k`は各設計パイプの2つの共通ノードを接続するアークのインデックス、`node_fr`は各設計パイプをモデル化するアークの尾部ノードのインデックス、`node_to`は各設計パイプをモデル化するアークの頭部ノードのインデックス、`des_pipes`は同じアーク`k`に沿って存在する設計パイプのベクトルです。`AbstractNCModel`タイプの場合、制約は追加されません。これらの定式化タイプでは、流れは方向によって分割されず、流れの境界は[`variable_flow`](@ref)での変数の初期化時に課されます。
