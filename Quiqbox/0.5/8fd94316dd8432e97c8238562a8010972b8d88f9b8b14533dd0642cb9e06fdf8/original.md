```
sortPermBasis(bs::AbstractArray{<:CompositeGTBasisFuncs{T, D}}; 
              roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector{Int}
```

Return a `Vector` of indices `I` such that `bs[I] ==`[`sortBasis`](@ref) `(bs; roundAtol)[I]`.
