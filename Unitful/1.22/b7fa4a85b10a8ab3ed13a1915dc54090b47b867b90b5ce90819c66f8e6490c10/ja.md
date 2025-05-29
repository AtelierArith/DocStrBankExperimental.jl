```
Quantity(period::Dates.FixedPeriod)
```

指定された `period` に対応する `Quantity` を作成します。結果の `Quantity` の数値は `Int64` 型です。

# 例

```jldoctest
julia> using Dates: Second

julia> Quantity(Second(5))
5 s
```
