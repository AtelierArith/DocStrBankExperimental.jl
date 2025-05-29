```
read_metadata(sim::Simulation, type::Union{Symbol, DataType}[, field::Symbol, key::Symbol ])
read_metadata(filename::String, type::Union{Symbol, DataType}[, field::Symbol, key::Symbol ])
```

Read metadata for a `field` of an agent- or edgetype or the `globals` or `params` struct (see [`create_simulation`](@ref)) or to a raster (in that case `field` must be the name of the raster). `type` must be an agent- or edgetype, or one of these symbols: :Global, :Param or :Raster. Metadata is stored via `key, value` pairs. Multiple pairs can be attached to a single field, a single piece of the metadata can be retrived via the `key` parameter. If this is not set (or set to Symbol()), a Dict{Symbol, Any} with the complete metadata of this field is returned. If also `field` is not set, the metadata of all fields are returned.

See also: [`write_metadata`](@ref)
