## COSINEKNN

```
compute the k-nearest neighbors similarity metric between the
vertices of A or the upper half of a bipartite graph A.
```

## Functions

  * S = cosineknn{T}(A::SparseMatrixCSC{T,Int64},K::Int64)
  * S = cosineknn(A::MatrixNetwork,K::Int64)

## Example

```
A = load_matrix_network("bfs_example")
S = cosineknn(A,2)
```
