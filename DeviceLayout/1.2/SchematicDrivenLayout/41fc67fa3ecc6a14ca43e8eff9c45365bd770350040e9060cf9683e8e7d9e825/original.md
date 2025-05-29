```
render!(cs::AbstractCoordinateSystem, obj::GeometryEntity, meta::DeviceLayout.Meta,
    target::LayoutTarget; kwargs...)
```

Render `obj` to `cs`, with metadata mapped to layers and rendering options by `target`.
