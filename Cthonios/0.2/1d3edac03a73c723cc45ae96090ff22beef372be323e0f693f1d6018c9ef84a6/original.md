```julia
struct Domain{C, D, S, DBCs, DDofs, NBCs, NS, CPs} <: Cthonios.AbstractDomain
```

  * `coords::Any`
  * `dof::Any`
  * `sections::Any`
  * `dirichlet_bcs::Any`
  * `dirichlet_dofs::Any`
  * `neumann_bcs::Any`
  * `neumann_bc_sections::Any`
  * `contact_pairs::Any`

Domain type to hold information like bcs, sections, etc. Note that the `DofManager` unknown dofs are not automatically set. After setting up a `Domain` you will need to run, `update_unknown_dofs!`.

`mesh` - Handle to an open `FileMesh`. `dof` - `DofManager` object. `sections` - A set of `SectionInternal`s. `dirichlet_bcs` - A set of `DirichletBCInternal`s. `dirichlet_dofs` - A set of dofs to apply dirichlet dofs.   This is mainly for book-keeping purposes
