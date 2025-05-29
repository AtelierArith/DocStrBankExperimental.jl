```
parse(::Type{BiasFunction}, value::String)::BiasFunction
```

`value`を解析して有効な[`BiasFunction`](@ref)列挙型を返します。

# 例外

  * `ArgumentError`: バイアスの説明が一致しない場合。
