```
M = bitinformation(A::AbstractArray{T}, mask::BitArray) where {T<:Union{Integer,AbstractFloat}}
```

Bitwise real information content of array `A` calculated from the bitwise mutual information in adjacent entries in A along dimension `dim` (optional keyword). Array `A` is masked through trues in entries of the mask `mask`. Masked elements are ignored in the bitwise information calculation.
