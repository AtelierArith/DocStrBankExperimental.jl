```
Epoch(ep::Epoch{S1}, scale::S2) where {S1, S2}
```

`ep`を、時間スケール`S1`の`Epoch`から、時間スケール`S2`の`Epoch`に変換します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> ep = TTEpoch(2000,1,1)
2000-01-01T00:00:00.000 TT

julia> Epoch(ep, TAI)
1999-12-31T23:59:27.816 TAI
```
