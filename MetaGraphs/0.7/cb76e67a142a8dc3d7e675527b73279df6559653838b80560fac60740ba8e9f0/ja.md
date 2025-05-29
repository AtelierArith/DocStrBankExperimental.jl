```
filter_edges(g, prop[, val])
filter_edges(g, fn)
```

プロパティ `prop` が定義されているすべてのエッジへのイテレータを返します（オプションで `val` として）、または関数 `fn` がイテレータに含めるべきエッジに対してのみ `true` を返す場合です。

`fn` は次の形式である必要があります。

```
fn(g::AbstractMetaGraph{T}, e::SimpleEdge{T})::Boolean
```

ここで `e` は評価されているエッジに置き換えられます。
