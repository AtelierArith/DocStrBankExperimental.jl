## FLOYDWARSHALL

```
compute all shortest paths using the Floyd-Warshall algorithm.

(D,P) = floydwarshall(A) returns the shortest distance matrix between all pairs
of nodes in the graph A in matrix D.  If A has a negative weight cycle, then this
algorithm will throw an error. P is the matrix of predecessors.
```

## Functions

  * (D,P) = floydwarshall(A::MatrixNetwork)
  * (D,P) = floydwarshall{T}(A::SparseMatrixCSC{T,Int64})

## Example

```
A = load_matrix_network("all_shortest_paths_example")
(D,P) = floydwarshall(A)
```
