## CORENUMS

```
compute the core number for each vertex in the graph and returns the core
numbers for each vertex of the graph A along with the removal order of the vertex in the 
tuple (d,rt). This function works on directed graphs but gives the in-degree core number.
To get the out-degree core numbers call corenums(A')
```

## Functions

  * (d,rt) = corenums(A::MatrixNetwork)
  * (d,rt) = corenums{T}(A::SparseMatrixCSC{T,Int64})
  * (d,rt) = corenums(ei::Vector{Int64},ej::Vector{Int64})

## Example

```
A = load_matrix_network("cores_example")
(d,rt) = corenums(A)
```
