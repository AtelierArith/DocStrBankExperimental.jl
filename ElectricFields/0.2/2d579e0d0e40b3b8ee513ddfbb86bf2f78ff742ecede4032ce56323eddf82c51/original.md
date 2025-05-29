```
Crystal(material, d, R=I; ω₀)
```

Convenience constructor for [`Crystal`](@ref); if a central angular frequency `ω₀` is provided, the linear slope of the dispersion of the `material` is computed at `ω₀`. This slope is subsequently subtracted from the dispersion.
