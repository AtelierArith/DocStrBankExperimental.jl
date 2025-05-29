```
mutable struct CoordinateSystem{S<:Coordinate} <: AbstractCoordinateSystem{S}
    name::String
    elements::Vector{GeometryEntity{S}}
    meta::Vector{Meta}
    refs::Vector{GeometryReference}
    create::DateTime

    CoordinateSystem{S}(x, y, ym, z, t) where {S} = new{S}(x, y, ym, z, t)
    CoordinateSystem{S}(x, y, ym, z) where {S} = new{S}(x, y, ym, z, now())
    CoordinateSystem{S}(x, y, ym) where {S} = new{S}(x, y, ym, GeometryReference[], now())
    CoordinateSystem{S}(x) where {S} =
        new{S}(x, GeometryEntity{S}[], Meta[], GeometryReference[], now())
    CoordinateSystem{S}() where {S} = begin
        c = new{S}()
        c.elements = GeometryEntity{S}[]
        c.meta = Meta[]
        c.refs = GeometryReference[]
        c.create = now()
        c
    end
end
```

A `CoordinateSystem` has a name and contains geometry entities (Polygons, Rectangles) and references to `GeometryStructure` objects. It also records the time of its own creation.

To add elements, use `place!`, or use `render!` to be agnostic between `CoordinateSystem` and `Cell`. To add references, use `addref!` or `addarr!`.
