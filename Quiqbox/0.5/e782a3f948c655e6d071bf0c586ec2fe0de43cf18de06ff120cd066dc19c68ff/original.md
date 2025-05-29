```
neAttraction(bf1::AbstractGTBasisFuncs{T, D, 1}, bf2::AbstractGTBasisFuncs{T, D, 1}, 
             nuc::Union{Tuple{String, Vararg{String, NNMO}}, AbstractVector{String}}, 
             nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})}) where {T, D, NNMO} -> 
T
```

Return the nuclear attraction between two basis functions, provided with the nuclei and  their coordinates (in the atomic units).
