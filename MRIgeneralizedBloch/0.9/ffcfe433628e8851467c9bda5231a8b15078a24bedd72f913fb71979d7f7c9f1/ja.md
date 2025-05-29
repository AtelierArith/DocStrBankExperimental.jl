```
greens_lorentzian(κ)
```

ローレンツ線形に対応するグリーン関数を評価します。ここで `κ = (t-τ)/T2s` です。

# 例

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_lorentzian((t-τ)/T2s)
4.5399929762484854e-5
```
