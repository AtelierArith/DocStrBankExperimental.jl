```
absoluteunit(::Units)
absoluteunit(::Quantity)
```

単位または量を指定すると、アフィンであるかどうかにかかわらず（例：`°C`）、対応する絶対温度スケールの単位（例：`K`）を返します。[`Unitful.ContextUnits`](@ref) オブジェクトを渡すと、同じ昇格単位を持つ別の `ContextUnits` オブジェクトが返されますが、これはアフィン単位である可能性があるため、注意してください。
