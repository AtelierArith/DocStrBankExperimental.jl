```
write_metadata(sim::Simulation, type::Union{Symbol, DataType}, field::Symbol, key::Symbol, value)
```

Attach metadata to a `field` of an agent- or edgetype or the `globals` or `params` struct (see [`create_simulation`](@ref)) or to a raster (in that case `field` must be the name of the raster). `type` must be an agent- or edgetype, or one of these symbols: :Global, :Param or :Raster. Metadata is stored via `key, value` pairs, so that multiple metadata can be attached to a single field.

See also: [`read_metadata`](@ref)
