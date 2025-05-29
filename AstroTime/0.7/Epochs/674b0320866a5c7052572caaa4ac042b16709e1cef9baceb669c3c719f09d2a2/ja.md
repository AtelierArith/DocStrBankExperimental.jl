```
modified_julian(ep)
```

エポック `ep` の修正ユリウス日を返します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> modified_julian(TAIEpoch(2000, 1, 1, 12))
51544.5 days
```
