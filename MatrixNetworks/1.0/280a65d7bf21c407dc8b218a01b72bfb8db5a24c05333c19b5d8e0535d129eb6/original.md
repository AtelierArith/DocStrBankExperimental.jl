## DFS

```
compute depth first search distances and returns the distance (d), the discover (dt),
the finish time(ft), and the predecessor array (pred) in the tuple (d,dt,ft, pred).

pred[i] = 0 if vertex i is in a component not reachable from u and i != u.
```

## Functions

  * (d,dt,ft,pred) = dfs(A::MatrixNetwork,u::Int64,full::Int64,target::Int64)
  * (d,dt,ft,pred) = dfs(A::MatrixNetwork,u::Int64)
  * (d,dt,ft,pred) = dfs{T}(A::SparseMatrixCSC{T,Int64},u::Int64,full::Int64,target::Int64)
  * (d,dt,ft,pred) = dfs{T}(A::SparseMatrixCSC{T,Int64},u::Int64)
  * (d,dt,ft,pred) = dfs(ei::Vector{Int64},ej::Vector{Int64},u::Int64,full::Int64,target::Int64)
  * (d,dt,ft,pred) = dfs(ei::Vector{Int64},ej::Vector{Int64},u::Int64)

## Example

```
A = load_matrix_network("dfs_example")
(d,dt,ft,pred)  = dfs(A,1)
```
