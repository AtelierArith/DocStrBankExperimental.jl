```
compute_peaceman_index(g::T, K, r, pos; kwarg...) where T<:Jutul.JutulMesh
```

Compute the Peaceman index for a given mesh.

# Arguments

  * `g::JutulMesh`: Reservoir mesh
  * `K`: Permeability tensor or scalar.
  * `r`: Well radius.
  * `pos`: Position of the well (index of cell or IJK truplet).
  * `kwarg...`: Additional keyword arguments passed onto inner version of function.

# Returns

  * The computed Peaceman index.
