```
UT1Epoch(year, month, day, hour=0, minute=0, second=0.0)
```

日付と時間のコンポーネントからUT1Epochを構築します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> UT1Epoch(2018, 2, 6, 20, 45, 0.0)
2018-02-06T20:45:00.000 UT1

julia> UT1Epoch(2018, 2, 6)
2018-02-06T00:00:00.000 UT1
```
