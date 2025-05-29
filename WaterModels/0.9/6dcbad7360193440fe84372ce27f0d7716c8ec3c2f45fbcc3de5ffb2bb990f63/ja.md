```
constraint_on_off_pump_head_gain(
    wm::AbstractPWLRDModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    q_min_forward::Float64
)
```

ポンプのヘッドゲインをモデル化する制約を追加します。ポンプが稼働している場合、流量の非線形関数の外部および区分線形内部近似を介して行われます。ポンプが非アクティブな場合、ヘッドゲインはゼロに制限されます。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はポンプのインデックス、`node_fr`はポンプのテールノードのインデックス、`node_to`はポンプのヘッドノードのインデックス、`q_min_forward`はポンプがアクティブなときの*最小*（正の）流量です。ヘッドゲインは非負であると仮定され、`node_fr`から`node_to`に向かって指示されます。
