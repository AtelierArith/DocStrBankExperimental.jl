```julia
SimulationBox(
    basis::AbstractMatrix{Float64},
    origin::AbstractVector{Float64},
    bc::MolecularDynamicsFiles.BoundaryConditions,
    istriclinic::Bool
) -> MolecularDynamicsFiles.SimulationBox

```

Construct simulation box. `basis` is a 3x3 matrix with simulation box vectors in columns. `origin` is a 3-component vector.
