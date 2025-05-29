```
AbstractIndexedGraph{T} <: AbstractGraph{T}
```

An abstract type representing an indexed graph. `AbstractIndexedGraph`s must have the following elements:

  * `A::SparseMatrixCSC` adjacency matrix
