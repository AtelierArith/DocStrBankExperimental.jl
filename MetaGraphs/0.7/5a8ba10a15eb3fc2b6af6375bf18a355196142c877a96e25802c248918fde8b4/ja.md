```
filter_vertices(g, prop[, val])
filter_vertices(g, fn)
```

プロパティ `prop` が定義されているすべての頂点（オプションで `val` として）へのイテレータを返すか、関数 `fn` がイテレータに含めるべき頂点に対してのみ `true` を返す場合です。

`fn` は次の形式である必要があります。

```
fn(g::AbstractMetaGraph, v::Integer)::Boolean
```

ここで `v` は評価される頂点に置き換えられます。
