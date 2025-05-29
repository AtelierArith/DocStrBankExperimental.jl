```
finish_assemble(a::COOAssembler) -> K, f
```

Finalize the assembly and return the sparse matrix `K::SparseMatrixCSC` and vector `f::Vector`. If the assembler have not been used for vector assembly, `f` is an empty vector.
