## CSRTOSPARSE

```
convert a matrix from compressed sparse row to a sparse matrix A.
It returns the arrays that feed the sparse function in julia.
```

## Functions

  * (nzi,nzj,nzv) = csr*to*sparse{T}(rp::Vector{Int64},ci::Vector{Int64},ai::Vector{T})
  * (nzi,nzj,nzv) = csr*to*sparse{T}(rp::Vector{Int64},ci::Vector{Int64},ai::Vector{T},nrows::Int64)

## Example

```
i = [1;2;3]
j = [3;4;4]
v = [8;9;10]
(rp,ci,ai,m) = sparse_to_csr(i,j,v)
(nzi,nzj,nzv) = csr_to_sparse(rp,ci,ai)
A = sparse(nzi,nzj,nzv,length(rp)-1,maximum(ci))
B = csr_to_sparse_matrix(rp,ci,ai)
isequal(A,B)
```
