```
cliptree(op::Clipper.ClipType, s::AbstractPolygon{S}, c::AbstractPolygon{T};
    kwargs...) where {S<:Coordinate, T<:Coordinate}
cliptree(op::Clipper.ClipType, s::AbstractVector{A}, c::AbstractVector{B};
    kwargs...) where {S, T, A<:AbstractPolygon{S}, B<:AbstractPolygon{T}}
cliptree(op::Clipper.ClipType,
    s::AbstractVector{Polygon{T}}, c::AbstractVector{Polygon{T}};
    pfs::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd,
    pfc::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd) where {T}

親子関係を持つポリゴンと内部の穴を表す `Clipper.PolyNode` を返します。単位と数値の型は変換する必要があるかもしれません。

[`Clipper`](http://www.angusj.com/delphi/clipper.php) ライブラリと [`Clipper.jl`](https://github.com/Voxel8/Clipper.jl) ラッパーを使用してポリゴンのクリッピングを行います。

## 位置引数

最初の引数はクリッピング操作を指定するために次のいずれかの型でなければなりません：

  * `Clipper.ClipTypeDifference`
  * `Clipper.ClipTypeIntersection`
  * `Clipper.ClipTypeUnion`
  * `Clipper.ClipTypeXor`

これらは型であることに注意してください。`()` を付けてはいけません。2番目と3番目の引数は `AbstractPolygon` またはそのベクトルです。

## キーワード引数

`pfs` と `pfc` はそれぞれ `s` と `c` 引数のポリゴンの塗りつぶしルールを指定します。これらの引数には以下が含まれる場合があります：

  * `Clipper.PolyFillTypeNegative`
  * `Clipper.PolyFillTypePositive`
  * `Clipper.PolyFillTypeEvenOdd`
  * `Clipper.PolyFillTypeNonZero`

詳細については [`Clipper` ドキュメント](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/PolyFillType.htm) を参照してください。
```
