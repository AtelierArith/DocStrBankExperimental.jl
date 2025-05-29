```
constraint_short_pipe_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
)
```

短いパイプの尾部ノードでの水頭を短いパイプの頭部ノードでの水頭と等しくする制約を追加します（すなわち、短いパイプには損失がないため）。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`は短いパイプのインデックス、`node_fr`は短いパイプの尾部ノードのインデックス、`node_to`は短いパイプの頭部ノードのインデックスです。
