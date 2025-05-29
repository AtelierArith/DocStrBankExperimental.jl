```
ginisimpson(v::Union{AbstractVector, AbstractSparseMatrix}) 
ginisimpson(abt::AbstractAbundanceTable, overwrite=false)
```

Computes the Gini-Simpson alpha diversity metric for a vector. When called on an `AbstractAbundanceTable`, returns a 1 x nsamples matrix with 1 entry per sample. See also [`ginisimpson!`](@ref).
