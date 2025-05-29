```
T4quartercyln(R::T, L::T, nR::IT, nL::IT; orientation = :b) where {T<:Number, IT<:Integer}
```

Four-node tetrahedron mesh of one quarter of solid  cylinder with given number of edges per radius.

The axis of the cylinder is along the Z axis. The mesh may be mirrored to create half a cylinder or a full cylinder.

Even though the orientation is controllable, for some orientations the mesh is highly distorted (`:a`, `:ca`, `:cb`). So a decent mesh can only be expected for the orientation `:b` (default).
