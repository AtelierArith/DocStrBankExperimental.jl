## BFS

```
compute breadth first search distances and returns a distance(d), 
the discover time(dt), predecessor array(pred) in the tuple (d,dt,pred)
pred[i] = 0 if vertex i is in a component not reachable from u and i != u.
Search stops when it hits the vertex target.
```

## Functions

  * (d,dt,pred) = bfs(A::MatrixNetwork,u::Int64,target::Int64)
  * (d,dt,pred) = bfs{T}(A::SparseMatrixCSC{T,Int64}),u::Int64,target::Int64)
  * (d,dt,pred) = bfs(ei::Vector{Int64},ej::Vector{Int64},u::Int64,target::Int64)

If target is not specified, it is assigned to 0

## Example

```
A = load_matrix_network("bfs_example")
(d,dt,pred) = bfs(A,1)
```
