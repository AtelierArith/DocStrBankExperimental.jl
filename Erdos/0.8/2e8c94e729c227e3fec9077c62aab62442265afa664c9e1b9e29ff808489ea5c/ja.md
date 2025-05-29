```
mutable struct EdgeMap{G <: AGraphOrDiGraph, T, D} <: AEdgeMap{T}
    g::G
    vtype::Type{T}
    data::D
end
```

エッジマップを実装する型。基盤となるコンテナ `data` は、辞書、行列、またはインデックス付きエッジを持つグラフ用のベクターであることができます。

```
EdgeMap{T}(g, ::Type{T})
```

グラフ `g` の頂点に型 `T` の値を関連付けるマップを返します。基盤となるストレージ構造はそれに応じて選択されます。

```
EdgeMap(g, data)
```

`data` を基盤となるストレージとして持つ EdgeMap を構築します。ストレージの型は行列または関連付けられた `edg => val` 型、またはインデックス付きエッジを持つグラフ用のベクターであることができます。

```
EdgeMap(g, f)
```

`edges(g)` の各 `e` に対して値 `f(e)` を持つエッジマップを構築します。
