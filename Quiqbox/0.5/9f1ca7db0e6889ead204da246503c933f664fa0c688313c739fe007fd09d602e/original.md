```
changeHbasis(b::GTBasis{T, D}, 
             nuc::Tuple{String, Vararg{String, NNMO}}, 
             nucCoords::Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, 
             C::Union{AbstractMatrix{T}, NTuple{2, AbstractMatrix{T}}}) where 
            {T, D, NNMO} -> 
NTuple{2, Any}
```

Return the one-body and two-body integrals after a change of basis based on the input `C`,  given the basis set information `b`. The type of each element in the returned `Tuple` is  consistent with the cases where the first argument of `changeHbasis` is an `AbstractArray`.
