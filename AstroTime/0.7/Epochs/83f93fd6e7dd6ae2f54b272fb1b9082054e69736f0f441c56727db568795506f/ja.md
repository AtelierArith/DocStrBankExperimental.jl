```
Epoch{S}(year, month, day, hour=0, minute=0, second=0.0) where S
```

日付と時間のコンポーネントから時間スケール `S` の `Epoch` を構築します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> Epoch{InternationalAtomicTime}(2018, 2, 6, 20, 45, 0.0)
2018-02-06T20:45:00.000 TAI

julia> Epoch{InternationalAtomicTime}(2018, 2, 6)
2018-02-06T00:00:00.000 TAI
```
