```
struct ClippedPolygon{T} <: AbstractPolygon{T}
    tree::Clipper.PolyNode{Point{T}}
end
```

クリッパーへの呼び出しによって定義された多角形のコレクション。
