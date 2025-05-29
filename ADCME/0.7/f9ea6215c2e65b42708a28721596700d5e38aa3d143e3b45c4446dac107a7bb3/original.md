```
SparseAssembler(handle::Union{PyObject, <:Integer}, n::Union{PyObject, <:Integer}, tol::Union{PyObject, <:Real}=0.0)
```

Creates a SparseAssembler for accumulating `row`, `col`, `val` for sparse matrices. 

  * `handle`: an integer handle for creating a sparse matrix. If the handle already exists, `SparseAssembler` return the existing sparse matrix handle. If you are creating different sparse matrices, the handles should be different.
  * `n`: Number of rows of the sparse matrix.
  * `tol` (optional): Tolerance. `SparseAssembler` will treats any values less than `tol` as zero.

# Example 1

```julia
handle = SparseAssembler(100, 5, 1e-8)
op1 = accumulate(handle, 1, [1;2;3], [1.0;2.0;3.0])
op2 = accumulate(handle, 2, [1;2;3], [1.0;2.0;3.0])
J = assemble(5, 5, [op1;op2])
```

`J` will be a [`SparseTensor`](@ref) object. 

# Example 2

```julia
handle = SparseAssembler(0, 5)
op1 = accumulate(handle, 1, [1;2;3], ones(3))
op2 = accumulate(handle, 1, [3], [1.])
op3 = accumulate(handle, 2, [1;3], ones(2))
J = assemble(5, 5, [op1;op2;op3]) # op1, op2, op3 are parallel
Array(run(sess, J))≈[1.0  1.0  2.0  0.0  0.0
                1.0  0.0  1.0  0.0  0.0
                0.0  0.0  0.0  0.0  0.0
                0.0  0.0  0.0  0.0  0.0
                0.0  0.0  0.0  0.0  0.0]
```
