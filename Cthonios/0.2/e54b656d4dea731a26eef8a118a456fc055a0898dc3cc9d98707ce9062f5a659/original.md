```julia
struct ExodusPostProcessor{Exo<:Exodus.ExodusDatabase} <: Cthonios.AbstractPostProcessor
```

  * `exo::Exodus.ExodusDatabase`
  * `solution_fields::Vector{String}`

Exodus post processor for writing quantities such as nodal, element, and quadrature fields to exodus files via `Exodus.jl`. `exo` - Handle to an open exodus database. `solution_fields` - A vector of names for solution fields on the nodes
