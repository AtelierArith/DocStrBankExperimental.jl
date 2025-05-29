```
sortBasisFuncs(bs::AbstractArray{<:FloatingGTBasisFuncs{T, D}}, 
               groupCenters::Bool=false; roundAtol::Real=getAtolVal(T)) where {T, D} -> 
Vector
```

Sort `FloatingGTBasisFuncs`. If `groupCenters = true`, Then the function will return an  `Vector{<:Vector{<:FloatingGTBasisFuncs}}` in which the elements are grouped basis  functions with same center coordinates. `roundAtol` specifies the absolute approximation  tolerance of comparing the center coordinates to determine whether they are treated as  "equal"; when set to `NaN`, no approximation will be made during the comparison.
