```
sortBasis(bs::Union{AbstractArray{<:CompositeGTBasisFuncs{T, D}}, 
                    Tuple{Vararg{CompositeGTBasisFuncs{T, D}}}}; 
          roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector{<:CompositeGTBasisFuncs{T, D}}
```

Sort basis functions. `roundAtol` specifies the absolute approximation tolerance of  comparing parameters stored in each `CompositeGTBasisFuncs` to determine whether they are  treated as "equal"; when set to `NaN`, no approximation will be made during the comparison.
