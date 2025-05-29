```
getoffset(ep::Epoch, scale::TimeScale)
```

与えられたエポック `ep` に対して、その時間スケールと別の時間 `scale` とのオフセットを秒単位で返します。

# 例

```jldoctest; setup = :(using AstroTime)
julia> tai = TAIEpoch(2000, 1, 1)
2000-01-01T00:00:00.000 TAI

julia> getoffset(tai, TT)
32.184
```
