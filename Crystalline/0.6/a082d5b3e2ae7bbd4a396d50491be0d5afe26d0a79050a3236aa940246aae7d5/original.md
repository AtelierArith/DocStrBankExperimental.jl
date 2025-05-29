```
conventionalize(op′::SymOperation, cntr::Char, modw::Bool=true) --> typeof(op)
```

Return a symmetry operation `op` $= \{W|w\}$ in a conventional setting, transformed from an input symmetry operation `op′` $≡ \{W'|w'\}$ in a primitive setting.

See [`primitivize(::SymOperation, ::Char, ::Bool)`](@ref) for description of the centering argument `cntr` and optional argument `modw`.
