```
push!(pacc::PairAccumulator, value::Number)
```

[`PairAccumulator`](@ref) のために `Base.push!` をオーバーロードします。このタイプのアキュムレーターには、一度に単一の `value <: Number` のみを `push!` することができます。
