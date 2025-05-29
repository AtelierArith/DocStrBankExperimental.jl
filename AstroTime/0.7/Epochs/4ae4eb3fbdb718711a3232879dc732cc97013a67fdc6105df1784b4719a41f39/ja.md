```
julian_twopart(ep)
```

エポック `ep` のための二部構成のユリウス日を返します。これはユリウス日数と日の分数からなるタプルです。

### 例

```jldoctest; setup = :(using AstroTime)
julia> julian_twopart(TAIEpoch(2000, 1, 2))
(2.451545e6 days, 0.5 days)
```
