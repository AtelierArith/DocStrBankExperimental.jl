```
cliptree(op::Clipper.ClipType, s::AbstractPolygon{S}, c::AbstractPolygon{T};
    kwargs...) where {S<:Coordinate, T<:Coordinate}
cliptree(op::Clipper.ClipType, s::AbstractVector{A}, c::AbstractVector{B};
    kwargs...) where {S, T, A<:AbstractPolygon{S}, B<:AbstractPolygon{T}}
cliptree(op::Clipper.ClipType,
    s::AbstractVector{Polygon{T}}, c::AbstractVector{Polygon{T}};
    pfs::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd,
    pfc::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd) where {T}
```

Return a `Clipper.PolyNode` representing parent-child relationships between polygons and interior holes. The units and number type may need to be converted.

Uses the [`Clipper`](http://www.angusj.com/delphi/clipper.php) library and the [`Clipper.jl`](https://github.com/Voxel8/Clipper.jl) wrapper to perform polygon clipping.

## Positional arguments

The first argument must be one of the following types to specify a clipping operation:

  * `Clipper.ClipTypeDifference`
  * `Clipper.ClipTypeIntersection`
  * `Clipper.ClipTypeUnion`
  * `Clipper.ClipTypeXor`

Note that these are types; you should not follow them with `()`. The second and third arguments are `AbstractPolygon`s or vectors thereof.

## Keyword arguments

`pfs` and `pfc` specify polygon fill rules for the `s` and `c` arguments, respectively. These arguments may include:

  * `Clipper.PolyFillTypeNegative`
  * `Clipper.PolyFillTypePositive`
  * `Clipper.PolyFillTypeEvenOdd`
  * `Clipper.PolyFillTypeNonZero`

See the [`Clipper` docs](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/PolyFillType.htm) for further information.
