```
edge_property(g, name)
```

グラフ `g` のエッジのプロパティ `name` に対応するエッジマップを返します。

```
edge_property(g)
```

要素 `property_name => edge_map` を持つ辞書を返します。

```
edge_property(g, e)
edge_property(g, u, v)
```

エッジ `e` に関連付けられたすべてのプロパティを含む `name => val` 形式の辞書を返します。

```
edge_property(g, e, name)
edge_property(g, u, v, name)
```

`edge_property(g, e)[name]` と同等です。

[`eprop`](@ref) はこの関数の短縮形です。
