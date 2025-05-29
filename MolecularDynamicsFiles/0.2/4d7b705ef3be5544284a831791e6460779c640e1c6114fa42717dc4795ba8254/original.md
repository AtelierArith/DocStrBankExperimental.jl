```julia
extra_scalars(
    frame::MolecularDynamicsFiles.MDFrame
) -> Dict{Symbol, Vector}

```

Return extra scalar properties of the particles.

Properties are considered 'extra' if none of the other MDFrame methods return that property. The properties not considered 'extra' are: `:id`, `:mol`, `:type`, `:x`, `:y`, `:z`, `:xs`, `:ys`, `:zs`, `:xu`, `:yu`, `:zu`, `:xsu`, `:ysu`, `:zsu`, `:ix`, `:iy`, `:iz`, `:vx`, `:vy`, `:vz`, `:element`, `:mass`
