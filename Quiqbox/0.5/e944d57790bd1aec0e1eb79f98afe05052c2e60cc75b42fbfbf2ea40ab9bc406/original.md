```
sortPermBasisFuncs(bs::Union{AbstractArray{<:FloatingGTBasisFuncs{T, D}}, 
                             Tuple{FloatingGTBasisFuncs{T, D}, 
                                   Vararg{FloatingGTBasisFuncs{T, D}}}}; 
                   roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector{Int}
```

Return a `Vector` of indices `I` such that `bs[I] ==`[`sortBasisFuncs`](@ref) `(bs; roundAtol)[I]`.
