```
sortBasis(b::GTBasis{T, D}; roundAtol::Real=getAtolVal(T)) where {T, D} -> 
GTBasis{T, D}
```

Reconstruct a [`GTBasis`](@ref) by sorting the `GTBasisFuncs` stored in the input one.
