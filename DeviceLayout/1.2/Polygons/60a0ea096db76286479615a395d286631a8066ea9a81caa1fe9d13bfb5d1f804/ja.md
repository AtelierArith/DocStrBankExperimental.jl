```
offset{S<:Coordinate}(s::AbstractPolygon{S}, delta::Coordinate;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
offset{S<:AbstractPolygon}(subject::AbstractVector{S}, delta::Coordinate;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
offset{S<:Polygon}(s::AbstractVector{S}, delta::Coordinate;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
```

[`Clipper`](http://www.angusj.com/delphi/clipper.php)ライブラリと[`Clipper.jl`](https://github.com/Voxel8/Clipper.jl)ラッパーを使用して、ポリゴンのオフセットを行います。

ポリゴンの向きは一貫している必要があり、外側のポリゴンは同じ向きを共有し、穴は反対の向きを持つ必要があります。さらに、穴は外側のポリゴン内に含まれている必要があります。穴のエッジをオフセットすると、コーナーで正のアーティファクトが生成される可能性があります。

最初の引数は[`AbstractPolygon`](@ref)である必要があります。2番目の引数はポリゴンをどれだけオフセットするかを指定します。キーワード引数には[結合タイプ](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/JoinType.htm)が含まれます：

  * `Clipper.JoinTypeMiter`
  * `Clipper.JoinTypeRound`
  * `Clipper.JoinTypeSquare`

また、[終了タイプ](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/EndType.htm)も含まれます：

  * `Clipper.EndTypeClosedPolygon`
  * `Clipper.EndTypeClosedLine`
  * `Clipper.EndTypeOpenSquare`
  * `Clipper.EndTypeOpenRound`
  * `Clipper.EndTypeOpenButt`
