```
constraint_des_pipe_selection(
    wm::AbstractWaterModel,
    n::Int,
    k::Int,
    node_fr::Int,
    node_to::Int,
    des_pipes::Array{Int,1}
)
```

アークごとに正確に1つの設計パイプが選択されることを保証する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`k`は複数の設計パイプを含むアークのインデックス、`node_fr`と`node_to`はアークを接続するノードインデックス、`des_pipes`は同じアーク`k`に存在する設計パイプのベクトルです。
