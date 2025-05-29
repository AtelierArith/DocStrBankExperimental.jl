```julia
pick_systems(
    systems::Array{Santiago.System},
    IDs::Array{T} where T<:AbstractString
) -> Vector{Santiago.System}

```

一致する `ID` を持つシステムを返します。空の配列を返すこともあります。
