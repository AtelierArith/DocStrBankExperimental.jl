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

Using the [`Clipper`](http://www.angusj.com/delphi/clipper.php) library and the [`Clipper.jl`](https://github.com/Voxel8/Clipper.jl) wrapper, perform polygon offsetting.

The orientations of polygons must be consistent, such that outer polygons share the same orientation, and any holes have the opposite orientation. Additionally, any holes should be contained within outer polygons; offsetting hole edges may create positive artifacts at corners.

The first argument should be an [`AbstractPolygon`](@ref). The second argument is how much to offset the polygon. Keyword arguments include a [join type](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/JoinType.htm):

  * `Clipper.JoinTypeMiter`
  * `Clipper.JoinTypeRound`
  * `Clipper.JoinTypeSquare`

and also an [end type](http://www.angusj.com/delphi/clipper/documentation/Docs/Units/ClipperLib/Types/EndType.htm):

  * `Clipper.EndTypeClosedPolygon`
  * `Clipper.EndTypeClosedLine`
  * `Clipper.EndTypeOpenSquare`
  * `Clipper.EndTypeOpenRound`
  * `Clipper.EndTypeOpenButt`
