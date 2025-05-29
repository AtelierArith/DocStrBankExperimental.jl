```julia
pick_systems(
    systems::Array{Santiago.System},
    IDs::Array{T} where T<:AbstractString
) -> Vector{Santiago.System}

```

Return systems with matching `ID`. May return an empty array.
