```julia
system_properties(
    frame::MolecularDynamicsFiles.MDFrame
) -> Dict{Symbol}

```

LAMMPSダンプの「units」や「time」、またはCFGの「A」や「R」など、他のシステムプロパティを返します。
