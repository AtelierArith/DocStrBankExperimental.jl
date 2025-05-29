```
clip(op::Clipper.ClipType, s, c; kwargs...) where {S<:Coordinate, T<:Coordinate}
clip(op::Clipper.ClipType, s::AbstractVector{A}, c::AbstractVector{B};
    kwargs...) where {S, T, A<:Polygon{S}, B<:Polygon{T}}
clip(op::Clipper.ClipType,
    s::AbstractVector{Polygon{T}}, c::AbstractVector{Polygon{T}};
    pfs::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd,
    pfc::Clipper.PolyFillType=Clipper.PolyFillTypeEvenOdd) where {T}
```

Return the `ClippedPolygon` resulting from a polygon clipping operation.

Uses the [`Clipper`](http://www.angusj.com/delphi/clipper.php) library and the [`Clipper.jl`](https://github.com/Voxel8/Clipper.jl) wrapper to perform polygon clipping.

## Positional arguments

The first argument must be one of the following types to specify a clipping operation:

  * `Clipper.ClipTypeDifference`
  * `Clipper.ClipTypeIntersection`
  * `Clipper.ClipTypeUnion`
  * `Clipper.ClipTypeXor`

Note that these are types; you should not follow them with `()`.

The second and third argument may be a `GeometryEntity` or array of `GeometryEntity`. All entities are first converted to polygons using [`to_polygons`](@ref). Each can also be a `GeometryStructure` or `GeometryReference`, in which case `elements(flatten(p))` will be converted to polygons. Each can also be a pair `geom => layer`, where `geom` is a `GeometryStructure` or `GeometryReference`, while `layer` is a `DeviceLayout.Meta`, a layer name `Symbol`, and/or a collection of either, in which case only the elements in those layers will be taken from the flattened structure.

## Keyword arguments

`pfs` and `pfc` specify polygon fill rules for the `s` and `c` arguments, respectively. These arguments may include:

  * `Clipper.PolyFillTypeNegative`
  * `Clipper.PolyFillTypePositive`
  * `Clipper.PolyFillTypeEvenOdd`
  * `Clipper.PolyFillTypeNonZero`

See the [`Clipper` docs](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/PolyFillType.htm) for further information.

See also [union2d](@ref), [difference2d](@ref), and [intersect2d](@ref).
