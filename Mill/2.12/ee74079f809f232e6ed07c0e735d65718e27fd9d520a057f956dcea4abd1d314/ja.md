```
LazyNode{Name, D, C} <: AbstractMillNode
```

データノードは、遅延方式でデータ型 `D` を格納し、オプションのメタデータ型 `C` を持ちます。

データのソースまたはその型は `Name` で指定されます。

参照: [`AbstractMillNode`](@ref), [`LazyModel`](@ref), [`Mill.unpack2mill`](@ref).
