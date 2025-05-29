```
MdofMesh(Elt, constrained_dofs, free_dofs)
```

Structure containing the data for building a mdof mesh

**Constructor**

  * `model`: Mdof model
  * `bc`: Boundary conditions

      * `:CC`: Clamped - Clamped
      * `:CF`: Clamped - Free
      * `:FF`: Free - Free

**Fields**

  * `Elt`: Element connectivity matrix
  * `constrained_dofs`: Constrained degrees of freedom
  * `free_dofs`: Free degrees of freedom
