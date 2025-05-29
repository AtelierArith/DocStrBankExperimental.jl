```
reconstruct(s::AbstractArray{<:AbstractArray{T,Φ}}, em)
```

Reconstruct the spatial timeseries `s` represented by a `Vector` of `AbstractArray` states using the embedding struct `em` of type [`AbstractSpatialEmbedding`](@ref).

Returns the reconstruction in the form of a `Dataset` (from `DelayEmbeddings`) where each row is a reconstructed state and they are ordered first through linear indexing into each state and then incrementing in time.
