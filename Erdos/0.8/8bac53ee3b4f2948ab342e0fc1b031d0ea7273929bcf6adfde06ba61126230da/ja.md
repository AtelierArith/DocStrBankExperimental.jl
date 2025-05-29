```
vertex_property(g, name)
```

グラフ `g` の頂点のプロパティ `name` に対応する頂点マップを返します。

```
vertex_property(g)
```

要素 `property_name => vertex_map` を持つ辞書を返します。

```
vertex_property(g, v)
```

頂点 `v` に関連付けられたすべてのプロパティを含む `name => val` 形式の辞書を返します。

```
vertex_property(g, v, name)
```

`vertex_property(g, v)[name]` と同等です。

[`vprop`](@ref) はこの関数の短縮形です。
