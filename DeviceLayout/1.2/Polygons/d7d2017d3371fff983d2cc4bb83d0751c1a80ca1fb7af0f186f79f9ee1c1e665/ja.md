```
struct StyleDict{S} <: GeometryEntityStyle where {S}
    styles::Dict{Vector{Int}, GeometryEntityStyle},
    default::S
end
```

`ClippedPolygon` または `CurvilinearRegion` 内の異なるレベルで異なるポリゴンに異なるスタイルを適用するために使用されるスタイル。スタイルは、対応する `Clipper.PolyNode` を `ClippedPolygon` 内で見つけるために必要な子インデックスのシーケンスによって保存されます。`CurvilinearRegion` の場合、深さ2の辞書（単一の親と1つの穴のセット）のみが有効です。
