```
conventionalize(v′::AbstractVec, cntr::Char)  -->  v::typeof(v′)
```

Transforms a primitive coordinate vector `v′` back to a standard conventional basis (specified by the centering type `cntr`), returning the conventional coordinate vector `v`.

See also [`primitivize`](@ref) and [`transform`](@ref).
