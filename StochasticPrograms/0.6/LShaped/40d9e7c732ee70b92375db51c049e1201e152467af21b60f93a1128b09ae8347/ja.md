```
DynamicAggregate(num_aggregates::Integer, rule::AbstractSelectionRule; lock_after::Function = (τ,n)->false)
```

[`DynamicAggregation`](@ref)のファクトリーオブジェクト。`LShaped.Optimizer`の`aggregate`に渡すか、[`Aggregator`](@ref)属性を設定します。パラメータの説明については?DynamicAggregationを参照してください。
