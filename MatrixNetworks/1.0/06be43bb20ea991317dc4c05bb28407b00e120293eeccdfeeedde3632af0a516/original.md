## CLUSTERCOEFFS

```
compute undirected clustering coefficients for a graph. clustercoeffs(A) computes a 
normalized, weighted clustering coefficients from a graph represented by a symmetric 
adjacency matrix A. clustercoeffs(A,weighted,normalized), with weighted and normalized 
boolean values indicating whether the computation has to be weighted and/or normalized.
```

## Functions

  * cc = clustercoeffs(A::MatrixNetwork,weighted::Bool,normalized::Bool)
  * cc = clustercoeffs{T}(A::SparseMatrixCSC{T,Int64},weighted::Bool,normalized::Bool)

If weighted and normalized are not specified, they are understood as true

## Example

```
A = load_matrix_network("clique-10")    
cc = clustercoeffs(MatrixNetwork(A))    
```
