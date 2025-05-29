```
my_artifacts_toml!(pkg::Union{Module,Base.UUID,Nothing}; versioned = false)
```

Return the path to (or creates) "Artifacts.toml" for the given `pkg`. If `versioned` is set to true,  we get a separate "Artifacts_<version number>.toml".

See also: [`@my_artifacts_toml!`](@ref)
