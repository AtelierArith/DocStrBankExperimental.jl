```
nnRepulsions(nuc::Union{Tuple{String, Vararg{String, NNMO}}, AbstractVector{String}}, 
             nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})}) where {NNMO, D, T} -> 
T
```

Return the nuclear repulsion energy given nuclei `nuc` and their coordinates `nucCoords`.
