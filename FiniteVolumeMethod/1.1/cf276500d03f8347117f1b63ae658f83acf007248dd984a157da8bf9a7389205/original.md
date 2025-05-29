```
InternalConditions(functions=();
    dirichlet_nodes::Dict{Int,Int}=Dict{Int,Int}(),
    dudt_nodes::Dict{Int,Int}=Dict{Int,Int}(),
    parameters::Tuple=ntuple(_ -> nothing, length(functions)))
```

This is a constructor for the [`InternalConditions`](@ref) struct, which holds the internal conditions for the PDE. See also [`Conditions`](@ref) (which [`FVMProblem`](@ref) wraps this into), [`ConditionType`](@ref), and [`BoundaryConditions`](@ref).

# Arguments

  * `functions::Union{<:Tuple,<:Function}=()`

The functions that define the internal conditions. These are the functions referred to in `edge_conditions` and `point_conditions`.

# Keyword Arguments

  * `dirichlet_nodes::Dict{Int,Int}=Dict{Int,Int}()`

A `Dict` that stores all [`Dirichlet`](@ref) points `u` as keys, with keys mapping to indices `idx` that refer to the corresponding condition function and parameters in `functions` and `parameters`.

  * `dudt_nodes::Dict{Int,Int}=Dict{Int,Int}()`

A `Dict` that stores all [`Dudt`](@ref) points `u` as keys, with keys mapping to indices `idx` that refer to the corresponding condition function and parameters in `functions` and `parameters`.

  * `parameters::Tuple=ntuple(_ -> nothing, length(functions))`

The parameters for the functions, with `parameters[i]` giving the argument `p` in `functions[i]`.

# Outputs

The returned value is the corresponding [`InternalConditions`](@ref) struct.

!!! note
    When the internal conditions get merged with the boundary conditions,  any internal conditions that are placed onto the boundary will  be replaced with the boundary condition at that point on the boundary.

