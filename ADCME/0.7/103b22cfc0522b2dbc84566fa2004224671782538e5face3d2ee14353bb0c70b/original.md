```
assemble(m::Union{PyObject, <:Integer}, n::Union{PyObject, <:Integer}, ops::PyObject)
```

Assembles the sparse matrix from the `ops` created by [`accumulate`](@ref). `ops` is either a single output from `accumulate`, or concated from several `ops`

```julia
op1 = accumulate(handle, 1, [1;2;3], [1.0;2.0;3.0])
op2 = accumulate(handle, 2, [1;2;3], [1.0;2.0;3.0])
op = [op1;op2] # equivalent to `vcat([op1, op2]...)`
```

`m` and `n` are rows and columns of the sparse matrix. 

See [`SparseAssembler`](@ref) for an example.
