```
bounds(s::GeometryStructure{T}) where {T <: Coordinate}
```

Return a `Rectangle{T}` bounding box around all objects in a structure or structures. Return a rectangle with zero width and height if the structures are empty.
