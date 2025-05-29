```
constraint_tank_volume(
    wm::AbstractWaterModel,
    i::Int;
    nw::Int=nw_id_default
)
```

タンクが非可動である場合に [`constraint_tank_volume_fixed`](@ref) 制約を追加するための制約テンプレート。通常、問題の最初の時間インデックスでタンクの初期容量を固定するために使用されます。ここで、`wm` は WaterModels オブジェクト、`i` は制約が追加されるタンクのインデックス（該当する場合）、`nw` は容量が固定されるサブネットワーク（または時間）インデックスです。
