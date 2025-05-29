```
constraint_on_off_pump_head_gain(
    wm::AbstractLAModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    q_min_forward::Float64
)
```

ポンプのヘッドゲインをモデル化する制約を追加します。ポンプが稼働している場合、これは流量の非線形関数の区分線形近似として表現されます。ポンプが非稼働の場合、ヘッドゲインはゼロに制限されます。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はポンプのインデックス、`node_fr`はポンプのテールノードのインデックス、`node_to`はポンプのヘッドノードのインデックス、`q_min_forward`はポンプが稼働しているときの*最小*（正の）流量です。ヘッドゲインは非負であると仮定され、`node_fr`から`node_to`に向かって指示されます。
