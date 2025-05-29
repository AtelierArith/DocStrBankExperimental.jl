```
BoundaryConditions(mesh::FVMGeometry, functions, conditions; parameters=nothing)
```

This is a constructor for the [`BoundaryConditions`](@ref) struct, which holds the boundary conditions for the PDE.  See also [`Conditions`](@ref) (which [`FVMProblem`](@ref) wraps this into), [`ConditionType`](@ref), and [`InternalConditions`](@ref).

# Arguments

  * `mesh::FVMGeometry`

The mesh on which the PDE is defined.

  * `functions::Union{<:Tuple,<:Function}`

The functions that define the boundary conditions. The `i`th function should correspond to the part of the boundary of  the `mesh` corresponding to the `i`th boundary index, as defined in DelaunayTriangulation.jl. 

  * `conditions::Union{<:Tuple,<:ConditionType}`

The classification for the boundary condition type corresponding to each boundary index as above. See  [`ConditionType`](@ref) for possible conditions - should be one of [`Neumann`](@ref), [`Dudt`](@ref), [`Dirichlet`](@ref), or [`Constrained`](@ref).

# Keyword Arguments

  * `parameters=ntuple(_ -> nothing, length(functions))`

The parameters for the functions, with `parameters[i]` giving the argument `p` in `functions[i]`.

# Outputs

The returned value is the corresponding [`BoundaryConditions`](@ref) struct.
