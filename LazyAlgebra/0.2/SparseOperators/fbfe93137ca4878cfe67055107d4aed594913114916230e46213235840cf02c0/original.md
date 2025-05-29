```
CompressedSparseOperator{F,T,M,N}
```

is an abstract sub-type of `SparseOperator{T,M,N}` and is inherited by the concrete types implementing sparse operators with compressed storage in format `F`.

Format `F` is specificed as a symbol and can be:

  * `:COO` for *Compressed Sparse Coordinate* storage format.  This format is not the most efficient, it is mostly used as an intermediate for building a sparse operator in one of the following formats.
  * `:CSC` for *Compressed Sparse Column* storage format.  This format is very efficient for applying the adjoint of the sparse operator.
  * `:CSR` for *Compressed Sparse Row* storage format.  This format is very efficient for directly applying the sparse operator.

To construct (or convert to) a sparse operator with compressed storage format `F`, you can call:

```
CompressedSparseOperator{F}(args...; kwds...)
CompressedSparseOperator{F,T}(args...; kwds...)
CompressedSparseOperator{F,T,M}(args...; kwds...)
CompressedSparseOperator{F,T,M,N}(args...; kwds...)
```

where given parameters `T`, `M` and `N`, arguments `args...` and optional keywords `kwds...` will be passed to the concrete constructor [`SparseOperatorCOO`](@ref), [`SparseOperatorCSC`](@ref) or [`SparseOperatorCSR`](@ref) corresponding to the format `F`.

It is possible to use a compressed sparse operator `A` as an iterator:

```julia
for (Aij,i,j) in A # simple but slow for CSR and CSC
    ...
end
```

to retrieve the values `Aij` and respective row `i` and column `j` indices for all the entries stored in `A`.  It is however more efficient to access them according to their storage order which depends on the compressed format.

  * If `A` is in CSC format:

    ```julia
    using LazyAlgebra.SparseMethods
    for j in each_col(A)        # loop over column index
        for k in each_off(A, j) # loop over structural non-zeros in this column
            i   = get_row(A, k) # get row index of entry
            Aij = get_val(A, k) # get value of entry
         end
    end
    ```
  * If `A` is in CSR format:

    ```julia
    using LazyAlgebra.SparseMethods
    for i in each_row(A)        # loop over row index
        for k in each_off(A, i) # loop over structural non-zeros in this row
            j   = get_col(A, k) # get column index of entry
            Aij = get_val(A, k) # get value of entry
         end
    end
    ```
  * If `A` is in COO format:

    ```julia
    using LazyAlgebra.SparseMethods
    for k in each_off(A)
         i   = get_row(A, k) # get row index of entry
         j   = get_col(A, k) # get column index of entry
         Aij = get_val(A, k) # get value of entry
    end
    ```

The low-level methods `each_row`, `each_col`, `each_off`, `get_row`, `get_col` and `get_val` are not automatically exported by `LazyAlgebra`, this is the purpose of the statement `using LazyAlgebra.SparseMethods`.
