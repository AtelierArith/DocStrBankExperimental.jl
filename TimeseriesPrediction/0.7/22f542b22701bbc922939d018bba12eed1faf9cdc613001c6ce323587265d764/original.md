```
SymmetricEmbedding(ste::SpatioTemporalEmbedding, sym::Tuple)
```

A `SymmetricEmbedding` is intended as a means of dimension reduction for a [`SpatioTemporalEmbedding`](@ref) by exploiting spatial symmetries in the system, listed as a `Tuple` of `<:Symmetry` (see [`Symmetry`](@ref)) for all possible symmetries.

All points at a time step equivalent to each other according to the symmetries passed in `sym` will be **averaged** to a single entry! For example, the symmetry `Reflection(2)` means that the embedding won't have two entries `u[i, j+1], u[i, j-1]` but instead a single entry `(u[i, j+1] + u[i, j-1])/2`, with `i,j` being indices *relative to the central point of the embedding*. (the same process is done for any index offset `j+2, j+3`, etc., depending on how large the spatial radius `r` is)

The resulting structure from `SymmetricEmbedding` can be used for reconstructing datasets in the same way as a [`SpatioTemporalEmbedding`](@ref).
