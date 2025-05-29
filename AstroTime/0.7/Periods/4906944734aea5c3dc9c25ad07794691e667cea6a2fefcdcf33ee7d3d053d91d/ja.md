```
unit(p::AstroPeriod)
```

周期 `p` の単位を返します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> unit(3.0seconds)
AstroTime.Periods.Second()
```
