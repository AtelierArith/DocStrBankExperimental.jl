## SCOMPONENTS

```
compute the strongly connected components of a graph

ci=scomponents(A) returns an index for the component number of every 
vertex in the graph A.  The total number of components is maximum(ci).
If the input is undirected, then this algorithm outputs just the 
connected components.  Otherwise, it output the strongly connected components.

The implementation is from Tarjan's 1972 paper: Depth-first search and 
linear graph algorithms. In SIAM's Journal of Computing, 1972, 1, 
pp.146-160.
```

## Functions

  * `cc = scomponents(A::MatrixNetwork)`
  * `cc = scomponents{T}(A::SparseMatrixCSC{T,Int64})`
  * `sci = strong_components_map(A::MatrixNetwork)`
  * `sci = strong_components_map{T}(A::SparseMatrixCSC{T,Int64})`
  * `sc_rich = enrich(cc::Strong_components_output) # check ?enrich for more`

## Example

```
A = load_matrix_network("cores_example")
cc = scomponents(A)
scomponents(A).number
scomponents(A).sizes      
scomponents(A).map  
strong_components_map(A)     # if you just want the map
enrich(scomponents(A)) # produce additional enriched output

# Can work on [ei,ej]
ei = [1;2;3]
ej = [2;4;1]
cc = scomponents(ei,ej)

# Can work on sparse matrix A
A = sprand(5,5,0.5)
cc = scomponents(A)
```
