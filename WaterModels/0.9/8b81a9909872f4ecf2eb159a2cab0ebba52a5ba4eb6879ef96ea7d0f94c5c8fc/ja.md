```
constraint_on_off_pump_power(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

[`constraint_on_off_pump_group`](@ref) 制約を追加するための制約テンプレートで、同じネットワークの同じ弧に沿って並行して動作する同一ポンプのグループに対してポンプの活性化ステータスの対称性を破る辞書順ソートを課します。ここで、`wm` は WaterModels オブジェクト、`k` はポンプグループのインデックス、`nw` はマルチネットワーク内のサブネットワークのインデックスです。
