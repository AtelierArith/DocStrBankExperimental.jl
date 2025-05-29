```
has_vertex(G::FlipGraphPlanar, g::TriangulatedPolygon) :: Bool
```

`g` が `G` の頂点である場合は `true` を返します。

`G` がモジュラー フリップ グラフである場合、`g` が頂点の適切な代表である場合にのみ `true` を返します。
