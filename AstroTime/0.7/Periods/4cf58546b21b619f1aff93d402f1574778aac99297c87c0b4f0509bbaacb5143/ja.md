```
value(p::AstroPeriod)
```

周期 `p` の単位なしの値を返します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> value(3.0seconds)
3.0
```
