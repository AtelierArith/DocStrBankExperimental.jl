```
constraint_on_off_pump_power_custom(
    wm::AbstractWaterModel,
    n::Int,
    a::Int,
    power_fixed::Float64,
    power_variable::Float64
)
```

ポンプの電力を流量の線形式として表現する制約を追加します。この線形式の係数は `power_fixed` と `power_variable` で与えられます。ここで、`wm` は WaterModels オブジェクト、`n` はマルチネットワーク内のサブネットワークのインデックス、`a` はポンプのインデックス、`power_fixed` はポンプが稼働していて流量がゼロのときに消費される電力の量（すなわち、電力対流量曲線の垂直軸でのゼロ流量の交点）、`power_variable` は流量単位あたりにポンプが消費する電力の量です。
