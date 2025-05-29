```
assembly(model::Mdof)
```

Assembly of the mass, stiffness and damping matrices of a mdof system

**Input**

  * `model`: Mdof model

**Outputs**

  * `K`: Stiffness matrix
  * `M`: Mass matrix
  * `C`: Damping matrix (if viscous dampers are defined in `model`)
