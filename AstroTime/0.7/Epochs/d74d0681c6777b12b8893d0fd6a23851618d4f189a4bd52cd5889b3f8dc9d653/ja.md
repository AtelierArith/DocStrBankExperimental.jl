```
Epoch{S2}(ep::Epoch{S1}) where {S1, S2}
```

`S1`の時間スケールを持つ`Epoch`である`ep`を、`S2`の時間スケールを持つ`Epoch`に変換します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> ep = TTEpoch(2000,1,1)
2000-01-01T00:00:00.000 TT

julia> TAIEpoch(ep)
1999-12-31T23:59:27.816 TAI
```
