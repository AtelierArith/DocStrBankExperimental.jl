```
clip(op::Clipper.ClipType, s, c; kwargs...) where {S<:Coordinate, T<:Coordinate}
clip(op::Clipper.ClipType, s::AbstractVector{A}, c::AbstractVector{B};
    kwargs...) where {S, T, A<:Polygon{S}, B<:Polygon{T}}
clip(op::Clipper.ClipType,
    s::AbstractVector{Polygon{T}}, c::AbstractVector{Polygon{T}};
    pfs::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd,
    pfc::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd) where {T}

ポリゴンクリッピング操作の結果として `ClippedPolygon` を返します。

[`Clipper`](http://www.angusj.com/delphi/clipper.php) ライブラリと [`Clipper.jl`](https://github.com/Voxel8/Clipper.jl) ラッパーを使用してポリゴンのクリッピングを行います。

## 位置引数

最初の引数はクリッピング操作を指定するために次のいずれかの型でなければなりません：

  * `Clipper.ClipTypeDifference`
  * `Clipper.ClipTypeIntersection`
  * `Clipper.ClipTypeUnion`
  * `Clipper.ClipTypeXor`

これらは型であることに注意してください。`()` を付けてはいけません。

2 番目と 3 番目の引数は `GeometryEntity` または `GeometryEntity` の配列である場合があります。すべてのエンティティは最初に [`to_polygons`](@ref) を使用してポリゴンに変換されます。それぞれは `GeometryStructure` または `GeometryReference` であることもでき、その場合 `elements(flatten(p))` はポリゴンに変換されます。それぞれは `geom => layer` のペアであることもでき、ここで `geom` は `GeometryStructure` または `GeometryReference` であり、`layer` は `DeviceLayout.Meta`、レイヤー名 `Symbol`、および/またはそれらのコレクションであり、その場合はフラット化された構造からそのレイヤー内の要素のみが取得されます。

## キーワード引数

`pfs` と `pfc` はそれぞれ `s` と `c` 引数のポリゴンフィルルールを指定します。これらの引数には次のものが含まれる場合があります：

  * `Clipper.PolyFillTypeNegative`
  * `Clipper.PolyFillTypePositive`
  * `Clipper.PolyFillTypeEvenOdd`
  * `Clipper.PolyFillTypeNonZero`

詳細については [`Clipper` ドキュメント](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/PolyFillType.htm) を参照してください。

また、[union2d](@ref)、[difference2d](@ref)、および [intersect2d](@ref) も参照してください。
```
