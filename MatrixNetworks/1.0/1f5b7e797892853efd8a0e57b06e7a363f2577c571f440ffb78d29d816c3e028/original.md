## SPARSETOCSR

```
convert sparse matrix into compressed row storage arrays
and returns the row pointer (rp), column index (ci) and value index (ai) arrays 
of a compressed sparse representation of the matrix A (or its triplet format storage)
```

## Functions

  * (rp,ci,ai,m) = sparse*to*csr{T}(A::SparseMatrixCSC{T,Int64})
  * (rp,ci,ai,m) = sparse*to*csr{T}(nzi::Array{Int64,1},nzj::Array{Int64,1},nzv::Array{T,1})

## Example

```
i = [1;2;3]
j = [3;4;4]
v = [8;9;10]
(rp,ci,ai,m) = sparse_to_csr(i,j,v)
```
