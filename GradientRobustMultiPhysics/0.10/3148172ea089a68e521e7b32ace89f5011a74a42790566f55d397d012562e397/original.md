```julia
add_boundarydata!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Int64,
    regions,
    btype::Type{<:GradientRobustMultiPhysics.AbstractBoundaryType};
    data,
    mask
) -> Vector{GradientRobustMultiPhysics.BoundaryData}

```

Adds the given boundary data with the specified AbstractBoundaryType at the specified position in the BoundaryOperator of the PDEDescription.

Note: If the data function is time-dependent (see User Data documentation) it is evaluated in any advance! step of a TimeControlSolver.
