```julia
add_extra_scalar!(
    frame::MolecularDynamicsFiles.MDFrame,
    name::Symbol,
    values::AbstractVector{Float64}
) -> AbstractVector{Float64}

```

Add an extra scalar particle property.

`name` may not be one of `:id`, `:mol`, `:type`, `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`, `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`, `:ix`, `:iy`, `:iz`, `:vx`, `:vy`, `:vz`, `:element`, `:mass`.   `values` must be of length `length(frame)`.   `values[i]` corresponds to the value of the added property of particle with id `id_tags(frame)[i]`.
