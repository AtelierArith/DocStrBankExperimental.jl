```
UnsatisfyableTransformer{T}(dataset::DataSet, types::Vector{QualifiedType})
```

要求されたのは、`types`のいずれかを提供できる変換器（型`T`）ですが、この制約を満たす変換器は存在しません。

# 例の発生

```julia-repl
julia> emptydata = DataSet(DataCollection(), "empty", SmallDict{String, Any}("uuid" => Base.UUID(rand(UInt128))))
DataSet empty

julia> read(emptydata, String)
ERROR: UnsatisfyableTransformer: "empty" に対して String を提供できるローダーは存在しません。定義されたローダーは次のとおりです:
Stacktrace: [...]
```
