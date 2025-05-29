```
save_trajectory([parser], file::AbstractString, systems::AbstractVector; kwargs...)
```

Save a trajectory given as a list of `AtomsBase`-compatible systems to a `file`. Providing a `parser` overwrites the automatic `AtomsIO` selection.
