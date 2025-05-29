```
CoordinateSystem(name::AbstractString)
```

Convenience constructor for `CoordinateSystem{typeof(1.0UPREFERRED)}`.

[`DeviceLayout.UPREFERRED`](@ref) is a constant set according to the `unit` preference in `Project.toml` or `LocalPreferences.toml`. The default (`"PreferNanometers"`) gives `const UPREFERRED = DeviceLayout.nm`, with mixed-unit operations preferring conversion to `nm`.
