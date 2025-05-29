```
constraint_on_off_pump_power(
    wm::AbstractLAModel,
    n::Int,
    a::Int,
    q_min_forward::Float64
)
```

ポンプが稼働している場合の電力消費を、より正確なモデルの（潜在的に）非線形関数の区分線形近似としてモデル化する制約を追加します。ポンプが非稼働の場合、電力はゼロに制限されます。ここで、`wm`はWaterModelsオブジェクト、`n`は考慮されるサブネットワーク（または時間）インデックス、`a`はポンプのインデックス、`q_min_forward`はポンプが稼働しているときの*最小*（正の）流量です。
