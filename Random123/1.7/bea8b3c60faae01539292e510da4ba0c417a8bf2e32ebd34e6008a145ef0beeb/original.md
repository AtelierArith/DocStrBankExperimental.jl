```
ars(key::Tuple{UInt128}, ctr::Tuple{UInt128}, rounds::Val{R})::Tuple{UInt128} where {R}
```

Functional variant of [`ARS1x`](@ref) and [`ARS4x`](@ref).  This function if free of mutability and side effects.
