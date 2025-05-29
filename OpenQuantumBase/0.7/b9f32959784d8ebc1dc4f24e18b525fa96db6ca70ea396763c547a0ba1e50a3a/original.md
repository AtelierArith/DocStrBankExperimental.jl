```
function ConstantCouplings(mats::Union{Vector{Matrix{T}},Vector{SparseMatrixCSC{T,Int}}}; unit=:h) where {T<:Number}
```

Constructor of `ConstantCouplings` object. `mats` is 1-D array of matrices. `str_rep` is the optional string representation of the coupling terms. `unit` is the unit one – `:h` or `:ħ`. The `mats` will be scaled by $2π$ is unit is `:h`.
