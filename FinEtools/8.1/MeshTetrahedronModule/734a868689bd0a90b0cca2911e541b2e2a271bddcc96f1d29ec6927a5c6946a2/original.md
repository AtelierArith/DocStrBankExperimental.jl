```
T10cylindern(R::T, L::T, nR::IT, nL::IT; orientation = :b) where {T<:Number, IT<:Integer}
```

Ten-node tetrahedron mesh of solid  cylinder with given number of edges per radius.

The axis of the cylinder is along the Z axis. 

Even though the orientation is controllable, for some orientations the mesh is highly distorted (`:a`, `:ca`, `:cb`). So a decent mesh can only be expected for the orientation `:b` (default).
