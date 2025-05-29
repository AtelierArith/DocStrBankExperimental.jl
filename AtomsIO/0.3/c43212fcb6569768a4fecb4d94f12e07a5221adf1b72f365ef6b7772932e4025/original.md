```
load_trajectory([parser], file::AbstractString; kwargs...)
```

Read a trajectory from a `file` and return a vector of `AtomsBase`-compatible structures. Providing a `parser` overwrites the automatic `AtomsIO` selection.
