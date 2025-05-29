```julia
MDFrame(
    timestep::Int64,
    box::MolecularDynamicsFiles.SimulationBox,
    particles::DataFrames.DataFrame,
    system_properties::Dict{Symbol}
) -> MolecularDynamicsFiles.MDFrame

```

MDFrameを構築します。
