```
assembly(model::OneDstructure, mesh::OneDMesh)
```

Compute the global stiffness and mass matrices for a 1D structure with a given mesh.

**Inputs**

  * `model`: OneDStructure

      * `Beam`: Beam model
      * `WaveEquation`: Bar, Rod or String model
  * `mesh`: OneDMesh

**Outputs**

  * `K`: global stiffness matrix
  * `M`: global mass matrix
