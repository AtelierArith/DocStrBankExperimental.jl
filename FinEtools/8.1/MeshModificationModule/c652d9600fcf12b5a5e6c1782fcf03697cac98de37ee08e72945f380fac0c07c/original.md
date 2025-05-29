```
meshboundary(fes::T) where {T<:AbstractFESet}
```

Compute the boundary of a mesh defined by the given finite element set.

# Arguments

  * `fes::T`: The finite element set representing the mesh.

# Returns

The boundary of the mesh.

Extract the finite elements of manifold dimension (n-1) from the supplied finite element set of manifold dimension (n).
