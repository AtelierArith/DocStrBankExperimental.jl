```
load_structure!(optimizer::AbstractStructuredOptimizer, structure::AbstractStochasticStructure, x₀::AbstractVector)
```

与えられた `structure` によってメモリ内に表現された確率的プログラムと初期決定 `x₀` で `optimizer` をインスタンス化します。

参照: [`optimize!`](@ref)
