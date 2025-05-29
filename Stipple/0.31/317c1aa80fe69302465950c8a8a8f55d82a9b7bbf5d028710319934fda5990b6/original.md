```
function Stipple.render(o::Reactive{T}, fieldname::Union{Symbol,Nothing} = nothing) where {T}
```

Default rendering of `Reactive` values. Specialize `Stipple.render` to define custom rendering for your type `T`.
