## DIJKSTRA

```
compute shortest paths using Dijkstra's algorithm.
d = dijkstra(A,u) computes the shortest path from vertex u to all nodes 
reachable from vertex u using Dijkstra's algorithm for the problem.  
The graph is given by the weighted sparse matrix A, where A(i,j) is 
the distance between vertex i and j.  In the output vector d, 
the entry d[v] is the minimum distance between vertex u and vertex v.
A vertex w unreachable from u has d(w)=Inf.
pred is the predecessor tree to generate the actual shorest paths. 
In the predecessor tree pred[v] is the vertex preceeding v in the 
shortest path and pred[u]=0. Any unreachable vertex has pred[w]=0 as well.  
If your network is unweighted, then use bfs instead.
```

## Functions

  * (d,pred) = dijkstra(A::MatrixNetwork,u::Int64)
  * (d,pred) = dijkstra{F}(A::SparseMatrixCSC{F,Int64},u::Int64)

## Example

```
# Find the minimum travel time between Los Angeles (LAX) and
# Rochester Minnesota (RST).

(A,xy,labels) = load_matrix_network_metadata("airports")
A = -A; # fix funny encoding of airport data
lax = 247; rst = 355
(d,pred) = dijkstra(A,lax)
@printf("Minimum time: %d",d[rst]); #Print the path
@printf("Path:")
u = rst
while(u != lax)
    @printf("%s <-- ", labels[u])
    u = pred[u];
    if (u == lax)
        @printf("%s", labels[lax])
    end
end
```
