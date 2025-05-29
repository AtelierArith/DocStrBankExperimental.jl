```
shannon(v::Union{AbstractVector, AbstractSparseMatrix}) 
shannon(abt::AbstractAbundanceTable)
```

Computes the Shannon alpha diversity metric for a vector. When called on an `AbstractAbundanceTable`, returns a 1 x nsamples matrix with 1 entry per sample. See also [`shannon!`](@ref).
