```
parse(::Type{PathRelinkingSelection}, value::String)::PathRelinkingSelection
```

`value`を解析して有効な[`PathRelinkingSelection`](@ref)列挙型を返します。

# 例外

  * `ArgumentError`: 選択の説明が一致しない場合。
