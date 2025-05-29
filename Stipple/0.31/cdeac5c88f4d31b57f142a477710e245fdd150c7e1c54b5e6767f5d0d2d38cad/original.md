```
function Stipple.render(val::T, fieldname::Union{Symbol,Nothing} = nothing) where {T}
```

Default rendering of value types. Specialize `Stipple.render` to define custom rendering for your types.
