```
-(a::Epoch, b::Epoch)
```

エポック `a` とエポック `b` の間の期間を返します。

### 例

```jldoctest; setup = :(using AstroTime)
julia> TAIEpoch(2018, 2, 6, 20, 45, 20.0) - TAIEpoch(2018, 2, 6, 20, 45, 0.0)
20.0 秒
```
