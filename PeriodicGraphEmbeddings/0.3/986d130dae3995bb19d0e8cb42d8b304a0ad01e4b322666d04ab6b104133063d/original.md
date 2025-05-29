```
function export_vtf(file::AbstractString, pge::PeriodicGraphEmbedding3D{T}, types=nothing, repeatedges=6, colorname=false, tostring=string, atomnumof==(a,i)->(a isa Integer ? a : i)) where T
```

Export a [`PeriodicGraphEmbedding3D`](@ref) to a .vtf `file` (readable by VMD).

If specified, `types` is a list of types for each vertex of `pge`. Each type is converted to string by the `tostring` function. The `atomnumof` function takes two arguments `ty` and `i` where `ty` is a type and `i` is the number of the vertex, and return an `Int` representing an atom number.
