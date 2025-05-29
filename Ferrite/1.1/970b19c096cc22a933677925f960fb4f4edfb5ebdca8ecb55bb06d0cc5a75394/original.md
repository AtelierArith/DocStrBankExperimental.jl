```
allocate_matrix(MatrixType, dh::DofHandler, args...; kwargs...)
```

Allocate a matrix of type `MatrixType` from the DofHandler `dh`.

This is a convenience method and is equivalent to:

`julia sp = init_sparsity_pattern(dh) add_sparsity_entries!(sp, dh, args...; kwargs...) allocate_matrix(MatrixType, sp)``

Refer to [`allocate_matrix`](@ref allocate_matrix(::Type{<:Any}, ::SparsityPattern)) for supported matrix types, and to [`init_sparsity_pattern`](@ref) for details about supported arguments `args` and keyword arguments `kwargs`.

!!! note
    If more than one sparse matrix is needed (e.g. a stiffness and a mass matrix) it is more efficient to explicitly create the sparsity pattern instead of using this method, i.e. use

    ```julia
    sp = init_sparsity_pattern(dh)
    add_sparsity_entries!(sp, dh)
    K = allocate_matrix(sp)
    M = allocate_matrix(sp)
    ```

    instead of

    ```julia
    K = allocate_matrix(dh)
    M = allocate_matrix(dh)
    ```

    Note that for some matrix types it is possible to `copy` the instantiated matrix (`M = copy(K)`) instead.

