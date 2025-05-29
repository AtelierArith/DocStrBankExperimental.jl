```
julian_period([T,] ep::Epoch; origin=:j2000, scale=timescale(ep), unit=days)
```

与えられたエポック `ep` に対して、時間スケール `scale` で表現された単位 `unit` におけるジュリアンエポック `origin` からの期間を返します。結果はデフォルトで [`AstroPeriod`](@ref) オブジェクトです。型引数 `T` が存在する場合、結果は `T` に変換されます。

### 例

```jldoctest; setup = :(using AstroTime)
julia> ep = TAIEpoch(2018, 2, 6, 20, 45, 0.0)
2018-02-06T20:45:00.000 TAI

julia> julian_period(ep; scale=TT)
6611.364955833334 days

julia> julian_period(ep; unit=years)
18.100929728496464 years

julia> julian_period(Float64, ep)
6611.364583333333
```
