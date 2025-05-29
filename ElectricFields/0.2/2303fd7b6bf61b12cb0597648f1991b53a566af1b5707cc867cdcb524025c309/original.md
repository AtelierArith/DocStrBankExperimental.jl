```
IsotropicMedium(material, d; ω₀)
```

Convenience constructor for [`IsotropicMedium`](@ref); if a central angular frequency `ω₀` is provided, the linear slope of the dispersion of the `material` is computed at `ω₀`. This slope is subsequently subtracted from the dispersion.
