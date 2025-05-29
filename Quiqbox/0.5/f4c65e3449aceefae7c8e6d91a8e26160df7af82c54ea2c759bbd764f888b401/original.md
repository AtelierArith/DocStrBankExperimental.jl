```
eeInteractions(bs::Union{Tuple{Vararg{AbstractGTBasisFuncs{T, D}}}, 
                         AbstractVector{<:AbstractGTBasisFuncs{T, D}}}) -> 
Array{T, 4}
```

Return the tensor of electron-electron interactions (in the chemists' notation) given a  basis set.
