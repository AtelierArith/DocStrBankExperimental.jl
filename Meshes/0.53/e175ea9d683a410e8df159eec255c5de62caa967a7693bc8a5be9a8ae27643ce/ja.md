```
HalfEdge(head, elem, prev, next, half)
```

`head` 頂点のインデックス、左側の `elem` における `prev` および `next` エッジのインデックス、そして反対の `half`-エッジのインデックスを格納します。一部の半エッジでは `elem` が `nothing` である場合があります。例えば、メッシュの境界エッジです。

詳細については [`HalfEdgeTopology`](@ref) を参照してください。
