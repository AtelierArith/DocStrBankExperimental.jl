```
timescale(ep)
```

エポック `ep` の時間スケールを返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> ep = TTEpoch(2000, 1, 1)
2000-01-01T00:00:00.000 TT

julia> timescale(ep)
TT
```
