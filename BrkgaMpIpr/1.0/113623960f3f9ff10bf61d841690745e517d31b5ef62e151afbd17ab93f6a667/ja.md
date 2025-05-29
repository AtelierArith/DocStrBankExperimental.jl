```
parse(::Type{PathRelinkingType}, value::String)::PathRelinkingType
```

`value`を解析して有効な[`PathRelinkingType`](@ref)列挙型を返します。

# 例外

  * `ArgumentError`: 型の説明が一致しない場合。
