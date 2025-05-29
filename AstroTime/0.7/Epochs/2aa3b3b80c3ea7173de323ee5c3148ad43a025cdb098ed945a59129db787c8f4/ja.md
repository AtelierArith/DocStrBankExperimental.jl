```
Epoch{S}(Δtai, ep::TAIEpoch) where S
```

`ep`を`TAIEpoch`から`Epoch`に変換します。ここで、`S`は時間スケールであり、`Δtai`を使用して`S2`と`TAI`の間のオフセットを上書きします。

### 例

```jldoctest; setup = :(using AstroTime)
julia> ep = TAIEpoch(2000,1,1)
2000-01-01T00:00:00.000 TAI

julia> TTEpoch(32.184, ep)
2000-01-01T00:00:32.184 TT
```
