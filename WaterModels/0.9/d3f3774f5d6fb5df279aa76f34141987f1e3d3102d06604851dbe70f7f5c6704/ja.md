```
constraint_on_off_pump_power_best_efficiency(
    wm::AbstractWaterModel,
    n::Int,
    a::Int,
    density::Float64,
    gravity::Float64,
    q_min_forward::Float64
)
```

ポンプの電力を流量の線形式として表現する制約を追加します。この線形式の係数は、ポンプが最適効率点で動作するという仮定を使用して計算されます。ここで、`wm`はWaterModelsオブジェクト、`n`はマルチネットワーク内のサブネットワークのインデックス、`a`はポンプのインデックス、`density`は水の密度、`gravity`は重力による加速度、`q_min_forward`はポンプが稼働しているとき（流れが前方に向かっているとき）の最小流量です。
