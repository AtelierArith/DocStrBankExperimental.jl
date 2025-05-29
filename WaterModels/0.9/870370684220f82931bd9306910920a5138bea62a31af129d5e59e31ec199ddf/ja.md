```
constraint_on_off_pump_head_gain(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    q_min_forward::Float64
)
```

ポンプのヘッドゲインを流量の非線形関数としてモデル化する制約を追加します。ポンプが非アクティブな場合、ヘッドゲインはゼロに制限されます。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はポンプのインデックス、`node_fr`はポンプのテールノードのインデックス、`node_to`はポンプのヘッドノードのインデックス、`q_min_forward`はポンプがアクティブなときの*最小*（正の）流量です。ヘッドゲインは、`node_fr`から`node_to`に向かう非負の量であると仮定されます。
