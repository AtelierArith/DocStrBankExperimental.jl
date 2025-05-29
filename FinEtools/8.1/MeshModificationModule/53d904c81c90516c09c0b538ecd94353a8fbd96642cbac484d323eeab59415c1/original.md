```
validate_mesh(fens, fes)
```

Validate the given mesh by checking if it satisfies certain sanity criteria.

# Arguments

  * `fens`: The finite element nodes of the mesh.
  * `fes`: The finite elements of the mesh.

Validate finite element mesh.

A finite element mesh given by the node set and the finite element set is validated by checking the sanity of the numbering:

  * the node numbers need to be positive and in serial order
  * the fe connectivity needs to refer to valid nodes
  * the finite element nodes need to be connected to at least one finite element

An error is reported as soon as it is detected.

# Returns

A boolean indicating whether the mesh is valid or not.
