```
j2000(ep)
```

エポック `ep` に対する J2000 ユリウス日を返します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> j2000(TAIEpoch(2000, 1, 1, 12))
0.0 days
```
