```
struct ScalarField{VF,M<:AbstractMesh,BC} <: AbstractScalarField
    values::VF  # scalar values at cell centre
    mesh::M     # reference to mesh
    BCs::BC     # store user-provided boundary conditions
end
```
