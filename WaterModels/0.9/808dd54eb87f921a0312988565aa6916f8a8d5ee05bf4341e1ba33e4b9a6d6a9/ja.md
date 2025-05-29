```
constraint_des_pipe_selection(
    wm::AbstractWaterModel,
    k::Int,
    node_fr::Int,
    node_to::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_des_pipe_selection`](@ref) 制約を追加するための制約テンプレートで、特定のアークに沿って構築される設計パイプを1つだけ選択することを強制します。ここで、`wm` は WaterModels オブジェクト、`k` は各設計パイプの2つの共通ノードを接続するアークのインデックス、`node_fr` は各設計パイプをモデル化するアークの尾ノードのインデックス、`node_to` は各設計パイプをモデル化するアークの先頭ノードのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
