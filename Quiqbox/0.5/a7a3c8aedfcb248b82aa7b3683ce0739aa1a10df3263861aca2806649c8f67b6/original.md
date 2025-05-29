```
mergeBasisFuncsIn(bs::Union{AbstractVector{<:GTBasisFuncs{T, D}}, 
                            Tuple{Vararg{GTBasisFuncs{T, D}}}}; 
                  roundAtol::Real=NaN) where {T, D} -> 
Vector{<:GTBasisFuncs{T, D}}
```

Try merging multiple `FloatingGTBasisFuncs` (if there's any) in `bs` into  `FloatingGTBasisFuncs{T, D, <:Any, <:Any, <:Any, ON}` where `ON > 1` if possible and then  return the resulted basis collection. If no merging is performed, then the returned  collection is same as (but not necessarily identical to) `bs`.
