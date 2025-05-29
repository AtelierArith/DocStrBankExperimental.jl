```
mutable struct VertexMap{G <: AGraphOrDiGraph, T, D} <: AVertexMap{T}
    g::G
    vtype::Type{T}
    data::D
end
```

頂点マップを実装する型。基盤となるコンテナ `data` は辞書またはベクターである可能性があります。

```
VertexMap{T}(g, ::Type{T})
```

グラフ `g` の頂点に型 `T` の値を関連付けるマップを返します。基盤となるストレージ構造はそれに応じて選択されます。

```
VertexMap(g, data)
```

`data` を基盤となるストレージとして持つ VertexMap を構築します。

```
VertexMap(g, f)
```

値 `f(u)` を持つ頂点マップを構築します（ここで `u` は `1:nv(g)` の範囲にあります）。
