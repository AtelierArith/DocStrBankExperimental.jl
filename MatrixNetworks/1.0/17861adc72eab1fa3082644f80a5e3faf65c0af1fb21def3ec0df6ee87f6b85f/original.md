## MST_PRIM

```
compute a minimum spanning tree with Prim's algorithm.
T = mst_prim_matrix(A) computes a minimum spanning tree T using Prim's algorithm
for the spanning tree of a graph with non-negative edge weights.

T = mst_prim_matrix(A,false) produces an MST for just the component at A containing
vertex 1.  T = mst_prim_matrix(A,0,u) produces the MST for the component
containing vertex u.

(ti,tj,tv,nverts) = mst_prim(A) returns the edges from the matrix and does not
convert to a sparse matrix structure.  This saves a bit of work and is
required when there are 0 edge weights.
```

## Functions

  * (ti,tj,tv,nverts) = mst_prim(A::MatrixNetwork,full::Bool,u::Int64)
  * (ti,tj,tv,nverts) = mst_prim(A::MatrixNetwork)
  * (ti,tj,tv,nverts) = mst_prim{T}(A::SparseMatrixCSC{T,Int64},full::Bool,u::Int64)
  * (ti,tj,tv,nverts) = mst_prim{T}(A::SparseMatrixCSC{T,Int64})
  * T = mst*prim*matrix(A::MatrixNetwork,full::Bool,u::Int64) #output modifier
  * T = mst*prim*matrix(A::MatrixNetwork) #output modifier
  * T = mst*prim*matrix{T}(A::SparseMatrixCSC{T,Int64},full::Bool,u::Int64) #output modifier
  * T = mst*prim*matrix{T}(A::SparseMatrixCSC{T,Int64}) #output modifier

## Example

```
A = load_matrix_network("airports")
A = -A #convert to travel time
A = max.(A,A')
A = sparse(A)
(ti,tj,tv,nverts) = mst_prim(A)
```
