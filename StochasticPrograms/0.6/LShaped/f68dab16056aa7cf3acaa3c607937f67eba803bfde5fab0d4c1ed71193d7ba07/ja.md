```
ClusterAggregate(rule::AbstractClusterRule; lock_after::Function = (τ,n)->false)
```

[`ClusterAggregation`](@ref)のファクトリーオブジェクト。`LShaped.Optimizer`の`aggregate`に渡すか、[`Aggregator`](@ref)属性を設定します。パラメータの説明については?ClusterAggregationを参照してください。
