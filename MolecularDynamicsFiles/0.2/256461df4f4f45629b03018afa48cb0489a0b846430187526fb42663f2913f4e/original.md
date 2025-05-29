```julia
images(
    frame::MolecularDynamicsFiles.MDFrame
) -> Vector{StaticArraysCore.SVector{3, Int16}}

```

Return image coordinates of particles in the system.  

Corresponds to properties `:ix`, `:iy`, `:iz`. Generates images from unwrapped coordinates if needed and possible.
