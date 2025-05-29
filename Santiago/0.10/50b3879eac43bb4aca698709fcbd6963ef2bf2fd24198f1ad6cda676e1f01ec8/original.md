```julia
templates_per_tech(
    systems::Array{Santiago.System}
) -> Dict{String, Set{String}}

```

List for every technology (including sources) the system templates it was used in. Note, only technologies that are used in at least one system are listed.
