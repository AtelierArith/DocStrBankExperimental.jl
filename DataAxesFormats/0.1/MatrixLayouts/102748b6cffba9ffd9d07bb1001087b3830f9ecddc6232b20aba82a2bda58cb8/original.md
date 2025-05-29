```
relayout!(destination::AbstractMatrix, source::AbstractMatrix)::AbstractMatrix
relayout!(destination::AbstractMatrix, source::NamedMatrix)::NamedMatrix
```

Return the same `matrix` data, but in the other memory layout.

Suppose you have a column-major UMIs matrix, whose rows are cells, and columns are genes. Therefore, summing the UMIs of a gene will be fast, but summing the UMIs of a cell will be slow. A `transpose` (no `!`) of a matrix is fast; it creates a zero-copy wrapper of the matrix with flipped axes, so its rows will be genes and columns will be cells, but in row-major layout. Therefore, **still**, summing the UMIs of a gene is fast, and summing the UMIs of a cell is slow.

In contrast, `transpose!` (with a `!`) (or [`transposer`](@ref)) is slow; it creates a rearranged copy of the data, also returning a matrix whose rows are genes and columns are cells, but this time, in column-major layout. Therefore, in this case summing the UMIs of a gene will be slow, and summing the UMIs of a cell will be fast.

!!! note
    It is almost always worthwhile to `relayout!` a matrix and then perform operations "with the grain" of the data, instead of skipping it and performing operations "against the grain" of the data. This is because (in Julia at least) the implementation of `transpose!` is optimized for the task, while the other operations typically don't provide any specific optimizations for working "against the grain" of the data. The benefits of a `relayout!` become even more significant when performing a series of operations (e.g., summing the gene UMIs in each cell, converting gene UMIs to fractions out of these totals, then computing the log base 2 of this fraction).


If you `transpose` (no `!`) the result of `transpose!` (with a `!`), you end up with a matrix that **appears** to be the same as the original (rows are cells and columns are genes), but behaves **differently** - summing the UMIs of a gene will be slow, and summing the UMIs of a cell is fast. This `transpose` of `transpose!` is a common idiom and is basically what `relayout!` does for you. In addition, `relayout!` will work for both sparse and dense matrices, and if `destination` is not specified, a `similar` matrix is allocated automatically for it.

!!! note
    The caller is responsible for providing a sensible `destination` matrix (sparse for a sparse `source`, dense for a non-sparse `source`). This can be a transposed matrix. If `source` is a `NamedMatrix`, then the result will be a `NamedMatrix` with the same axes. If `destination` is also a `NamedMatrix`, then its axes must match `source`.

