```
constraint_on_off_pump_switch(
    wm::AbstractWaterModel,
    a::Int;
    network_ids::Array{Int,1};
    kwargs...
)
```

[`constraint_on_off_pump_switch`](@ref) 制約を追加するための制約テンプレートで、これは多期間ポンプスケジューリング問題においてポンプがオフからオンに切り替えられる回数を制限します。ここで、`wm` は WaterModels オブジェクト、`a` はポンプのインデックス、`network_ids` は切り替え回数を制限するために使用されるネットワーク（時間）インデックスです。
