```
bigmat,bigmatasm,bigvecasm,bigvecdis = prepare(pattern)
```

Prepare for the assembly of sparse blocks into a large sparse matrix.  `bigmat` is allocated, with the correct sparsity structure, but its `nzval` undef'ed.     Where some blocks share the same sparsity structure, `blocks` in `pattern` can have `===` elements.

`pattern` is a `SparseMatrixCSC{<:SparseMatrixCSC}`, where empty blocks are structuraly zero

See also: [`addin!`](@ref)
