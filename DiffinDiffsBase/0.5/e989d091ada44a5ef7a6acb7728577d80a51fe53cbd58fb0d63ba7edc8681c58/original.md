```
post!(f, r; kwargs...)
```

Export result `r` in a default [`ExportFormat`](@ref).

The default format can be retrieved via [`getexportformat`](@ref) and modified via [`setexportformat!`](@ref). The keyword arguments that can be accepted depend on the format and the type of `r`.
