```
MeshElement(nodenum, material, theta)
```

An element in the mesh, consisting of four ordered nodes, a material, and a fiber orientation.

# Arguments

  * `nodenum::Vector{integer}`: Node indices, defined counterclockwise starting from the   bottom left node (as defined in the local coordinate system, see the figure).
  * `material::Material`: Material properties
  * `theta::float`: Fiber orientation
