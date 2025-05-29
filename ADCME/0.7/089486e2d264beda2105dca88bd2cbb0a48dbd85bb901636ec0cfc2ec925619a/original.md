```
accumulate(handle::PyObject, row::Union{PyObject, <:Integer}, cols::Union{PyObject, Array{<:Integer}}, vals::Union{PyObject, Array{<:Real}})
```

Accumulates `row`-th row. It adds the value to the sparse matrix

```julia
for k = 1:length(cols)
    A[row, cols[k]] += vals[k]
end
```

`handle` is the handle created by [`SparseAssembler`](@ref). 

See [`SparseAssembler`](@ref) for an example.

!!! note
    The function `accumulate` returns a `op::PyObject`. Only when `op` is executed, the nonzero values are populated into the sparse matrix.

