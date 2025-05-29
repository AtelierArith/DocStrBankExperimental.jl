```
attach!(g::SchematicGraph,
    pathnode::S,
    nodehook2::Pair{T, Symbol},
    position;
    i=lastindex(component(pathnode)),
    location=0) where {S <: ComponentNode, T <: ComponentNode}
使用法: attach!(g, pathnode, node2=>:hook2, position; i=segment_idx, location=0)
```

`g`に`pathnode`と`node2`の間にエッジを追加し、`pathnode`に沿った指定されたポイントに`:hook2`を接続します。

新しい`HandedPointHook`が、`i`で指定されたセグメントに沿って`position`の距離で生成されます。`location`が+1または-1の場合、生成されたフックはパスのスタイルで定義された範囲によってセグメントの右または左にオフセットされ、フックの内向きの方向はセグメントに戻るように指します。
