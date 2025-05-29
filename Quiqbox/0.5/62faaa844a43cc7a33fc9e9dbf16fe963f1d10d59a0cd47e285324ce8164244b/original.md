```
overlaps(bs::Union{Tuple{Vararg{AbstractGTBasisFuncs{T, D}}}, 
                   AbstractVector{<:AbstractGTBasisFuncs{T, D}}}) where {T, D} -> 
Matrix{T}
```

Return the orbital overlap matrix given a basis set.
