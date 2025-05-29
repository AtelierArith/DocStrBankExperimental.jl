```
CommunityProfile{T, F, S} <: AbstractAbundanceTable{T, F, S}
```

An `AbstractAssemblage` from [EcoBase.jl](https://github.com/EcoJulia/EcoBase.jl) that uses a `SparseMatrixCSC` under the hood.

`CommunityProfile`s are tables with `AbstractFeature`-indexed rows and `AbstractSample`-indexed columns. Note - we can use the `name` of samples and features to index.
