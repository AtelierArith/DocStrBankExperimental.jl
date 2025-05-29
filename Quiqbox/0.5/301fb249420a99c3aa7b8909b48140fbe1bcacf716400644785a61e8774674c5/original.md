```
eKinetics(bs::Union{Tuple{Vararg{AbstractGTBasisFuncs{T, D}}}, 
                    AbstractVector{<:AbstractGTBasisFuncs{T, D}}}) where {T, D} -> 
Matrix{T}
```

Return the electron kinetic energy matrix given a basis set.
