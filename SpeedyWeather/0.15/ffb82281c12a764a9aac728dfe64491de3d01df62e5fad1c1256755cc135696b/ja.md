```julia
initialize!(
    geopotential::SpeedyWeather.Geopotential,
    model::SpeedyWeather.PrimitiveEquation
)

```

ジオポテンシャルの垂直統合のための定数を事前計算します。ジオポテンシャルは次のように定義されます。

`Φ_{k+1/2} = Φ_{k+1} + R*T_{k+1}*(ln(p_{k+1}) - ln(p_{k+1/2}))`（半レベル） `Φ_k = Φ_{k+1/2} + R*T_k*(ln(p_{k+1/2}) - ln(p_k))`（全レベル）

同じ式ですが、`k → k-1/2`です。
