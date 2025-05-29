```julia
random_empty_patch(
    model::EasyABM.SpaceModel3D
) -> Union{Nothing, Tuple{Int64, Int64, Int64}}

```

Returns a random patch where no agents are present. Returns nothing if there is no such patch.
