```julia
struct DirichletBC{N, D, F} <: Cthonios.AbstractBCInput
```

  * `nset_name::Any`
  * `dofs::Any`
  * `func::Any`

Base Dirichlet boundary condition type used  for inputs either from a script or input file.  `nset_name` corresponds to the name of the  node set in the exodus file, `dofs` correspond to the indexed fields this bc is to be applied to, and `func` is the function to apply to the fields.
