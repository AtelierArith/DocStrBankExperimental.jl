```
genBasisFuncText(bs::Union{AbstractVector{<:FloatingGTBasisFuncs{T, D}}, 
                           Tuple{Vararg{FloatingGTBasisFuncs{T, D}}}}; 
                 norm::Real=1.0, printCenter::Bool=true, 
                 groupCenters::Bool=true, roundDigits::Int=-1) where {T, D} -> 
Vector{String}
```

Generate the text of input basis set (consisting of `FloatingGTBasisFuncs`). `norm` is the  additional normalization factor. `groupCenters` determines whether the function will group  the basis functions with same center together.
