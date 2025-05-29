```
Conditions{F} <: AbstractConditions
```

This is a `struct` that holds the boundary and internal conditions for the PDE. The constructor is 

```
Conditions(mesh::FVMGeometry, bc::BoundaryConditions, ic::InternalConditions=InternalConditions())
```

The fields are:

# Fields

  * `neumann_conditions::Dict{NTuple{2,Int},Int}`

A `Dict` that stores all [`Neumann`](@ref) edges `(u, v)` as keys, with keys mapping to indices  `idx` that refer to the corresponding condition function and parameters in `functions`.

  * `constrained_conditions::Dict{NTuple{2,Int},Int}`

A `Dict` that stores all [`Constrained`](@ref) edges `(u, v)` as keys, with keys mapping to indices `idx` that refer to the corresponding condition function and parameters in `functions`.

  * `dirichlet_conditions::Dict{Int,Int}`

A `Dict` that stores all [`Dirichlet`](@ref) points `u` as keys, with keys mapping to indices `idx` that refer to the corresponding condition function and parameters in `functions`.

  * `dudt_conditions::Dict{Int,Int}`

A `Dict` that stores all [`Dudt`](@ref) points `u` as keys, with keys mapping to indices `idx` that refer to the corresponding condition function and parameters in `functions`.

  * `functions::F<:Tuple`

The functions that define the boundary and internal conditions. The `i`th function should correspond to the part of the boundary of the `mesh` corresponding to the `i`th boundary index, as defined in DelaunayTriangulation.jl. The `i`th function is stored  as a [`ParametrisedFunction`](@ref).
