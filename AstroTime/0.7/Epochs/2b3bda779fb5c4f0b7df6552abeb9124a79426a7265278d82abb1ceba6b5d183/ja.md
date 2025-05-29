```
julian(ep)
```

エポック `ep` のユリウス日を返します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> julian(TAIEpoch(2000, 1, 1, 12))
2.451545e6 日
```
