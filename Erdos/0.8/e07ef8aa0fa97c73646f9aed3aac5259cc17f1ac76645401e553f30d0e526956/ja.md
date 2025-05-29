```
struct IndexedEdge <: AIndexedEdge
    src::Int
    dst::Int
    idx::Int
end
```

インデックス付きエッジタイプ

```
IndexedEdge(u, v) = IndexedEdge(u,v,-1)
```

無効なインデックスを持つエッジを作成します。
