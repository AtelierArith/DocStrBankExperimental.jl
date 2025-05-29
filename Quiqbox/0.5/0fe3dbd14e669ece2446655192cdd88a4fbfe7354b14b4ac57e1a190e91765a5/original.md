```
neAttractions(bs::Union{Tuple{Vararg{AbstractGTBasisFuncs{T, D}}}, 
                        AbstractVector{<:AbstractGTBasisFuncs{T, D}}}, 
              nuc::Union{Tuple{String, Vararg{String, NNMO}}, AbstractVector{String}}, 
              nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})}) where {T, D, NNMO} -> 
Matrix{T}
```

Return the nuclear attraction matrix given a basis set and the corresponding nuclei with  their coordinates (in atomic units).
