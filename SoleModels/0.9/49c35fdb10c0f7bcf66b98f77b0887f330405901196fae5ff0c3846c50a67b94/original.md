```
info(m::AbstractModel)::NamedTuple = m.info
info(m::AbstractModel, key) = m.info[key]
info(m::AbstractModel, key, defaultval)
```

Return the `info` structure for model `m`; this structure is used for storing additional information that does not affect the model's behavior.

This structure can hold, for example, information about the model's statistical performance during the learning phase.

See also [`AbstractModel`](@ref), [`info!`](@ref).
