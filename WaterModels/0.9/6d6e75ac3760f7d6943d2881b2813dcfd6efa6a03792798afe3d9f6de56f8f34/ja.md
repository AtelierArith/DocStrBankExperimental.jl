```
constraint_on_off_pump_switch(
    wm::AbstractWaterModel,
    a::Int,
    network_ids::Array{Int,1},
    max_switches::Int
)
```

ポンプのオンとオフの切り替え回数を制限する制約を追加します。ここで、`wm`はWaterModelsオブジェクト、`a`はポンプのインデックス、`network_ids`は切り替え回数を制限するために使用されるネットワーク（時間）インデックスの配列、`max_switches`はネットワークインデックスのセットに対して許可されるポンプの最大切り替え回数です。
