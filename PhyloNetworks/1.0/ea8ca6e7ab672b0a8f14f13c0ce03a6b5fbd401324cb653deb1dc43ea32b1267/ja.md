```
isparentof(node, edge)
ischildof(node, edge)
```

`true` なら `node` は `edge` の尾 / 頭、または親 / 子です。そうでなければ `false` です。エッジの方向が正しいと仮定し、そのフィールド `ischild1` が信頼できる（ルーティングと同期している）ことを意味します。

参照: [`getparent`](@ref), [`getchild`](@ref), [`isrootof`](@ref)
