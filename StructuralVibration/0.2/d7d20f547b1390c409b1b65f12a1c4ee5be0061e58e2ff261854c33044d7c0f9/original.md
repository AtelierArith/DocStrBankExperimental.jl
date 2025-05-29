```
OneDMesh(model, xmin, Nelt, bc)
```

Construct a mesh for a beam with Nelt elements, length L and starting at xmin.

**Constructor parameters**

  * `model`: Structure containing the data related to the 1D system
  * `xmin`: starting position of the beam
  * `Nelt`: number of elements
  * `bc`: Boundary conditions type

      * `:CC`: Clamped - Clamped
      * `:FF`: Free - Free
      * `:CF`: Clamped - Free
      * `:SS`: Simply Supported - Simply Supported (specific to beam)
      * `:CS`: Clamped - Simply Supported (specific to beam)
      * `:SF`: Simply Supported - Free (specific to beam)

**Fields**

  * `xmin`: Starting position of the beam
  * `L`: Length of the beam
  * `Nodes`: Nodes of the mesh
  * `Elt`: Elements of the mesh
  * `Ndof_per_node``: Number of degrees of freedom per node
  * `elem_size`: Size of the elements
  * `constrained_dofs`: Constrained degrees of freedom
  * `free_dofs`: Free degrees of freedom
