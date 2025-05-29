```
mutable struct Path{T<:Coordinate} <: GeometryStructure{T}
```

Type for abstracting an arbitrary styled path in the plane. Iterating returns [`Paths.Node`](@ref) objects.

Convenience constructors for `Path{T}` object:

```
Path{T}(p0::Point=zero(Point{T}), α0::typeof(1.0°)=0.0°, metadata::Meta=UNDEF_META)
Path{T}(name::String, p0::Point=zero(Point{T}), α0::Float64=0.0, metadata::Meta=UNDEF_META)
Path(p0::Point=zero(Point{typeof(1.0UPREFERRED)}); α0=0.0, name=uniquename("path"), metadata=UNDEF_META)
Path(p0x::Coordinate, p0y::Coordinate; α0=0.0, name=uniquename("path"), metadata=UNDEF_META)
Path(u::CoordinateUnits; α0=0.0, name=uniquename("path"), metadata=UNDEF_META)
Path(v::Vector{Node{T}}; name=uniquename("path"), metadata=UNDEF_META) where {T}
```
