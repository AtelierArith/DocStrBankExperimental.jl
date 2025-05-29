```
constraint_pipe_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int
)
```

パイプに沿ったヘッド差（損失）を制限する制約を追加します。これは、そのパイプに接続されているノードのヘッド変数の下限と上限に基づいています。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はパイプのインデックス、`node_fr`はパイプのテールノードのインデックス、`node_to`はパイプのヘッドノードのインデックスです。
