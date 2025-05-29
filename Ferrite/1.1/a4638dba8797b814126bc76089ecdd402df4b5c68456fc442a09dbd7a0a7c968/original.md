```
start_assemble(K::AbstractSparseMatrixCSC;            fillzero::Bool=true) -> CSCAssembler
start_assemble(K::AbstractSparseMatrixCSC, f::Vector; fillzero::Bool=true) -> CSCAssembler
```

Create a `CSCAssembler` from the matrix `K` and optional vector `f`.

```
start_assemble(K::Symmetric{AbstractSparseMatrixCSC};                 fillzero::Bool=true) -> SymmetricCSCAssembler
start_assemble(K::Symmetric{AbstractSparseMatrixCSC}, f::Vector=Td[]; fillzero::Bool=true) -> SymmetricCSCAssembler
```

Create a `SymmetricCSCAssembler` from the matrix `K` and optional vector `f`.

`CSCAssembler` and `SymmetricCSCAssembler` allocate workspace necessary for efficient matrix assembly. To assemble the contribution from an element, use [`assemble!`](@ref).

The keyword argument `fillzero` can be set to `false` if `K` and `f` should not be zeroed out, but instead keep their current values.
