```
info!(m::AbstractModel, info::NamedTuple; replace::Bool=false)
info!(m::AbstractModel, key, val)
```

Overwrite the `info` structure within `m`.

# Keyword Arguments

  * `replace::Bool`: overwrite the entire info structure.

See also [`AbstractModel`](@ref), [`info`](@ref).
