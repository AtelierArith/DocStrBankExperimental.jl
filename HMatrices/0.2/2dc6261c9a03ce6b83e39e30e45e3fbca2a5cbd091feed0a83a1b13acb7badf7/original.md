```
assemble_hmatrix([T,], K, rowtree, coltree;
    adm=StrongAdmissibilityStd(),
    comp=PartialACA(),
    threads=true,
    distributed=false,
    global_index=true)
```

Main routine for assembling a hierarchical matrix. The argument `K` represents the matrix to be approximated, `rowtree` and `coltree` are tree structure partitioning the row and column indices, respectively, `adm` can be called on a node of `rowtree` and a node of `coltree` to determine if the block is compressible, and `comp` is a function/functor which can compress admissible blocks.

It is assumed that `K` supports `getindex(K,i,j)`, and that `comp` can be called as `comp(K,irange::UnitRange,jrange::UnitRange)` to produce a compressed version of `K[irange,jrange]` in the form of an [`RkMatrix`](@ref).

The type paramter `T` is used to specify the type of the entries of the matrix, by default is inferred from `K` using `eltype(K)`.
