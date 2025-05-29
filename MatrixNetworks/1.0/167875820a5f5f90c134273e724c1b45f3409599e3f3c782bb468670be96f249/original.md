## BIPARTITE MATCHING

```
return a maximum weight bipartite matching of a graph
```

## Functions

  * Matching*Setup = bipartite*matching_setup{T}(A::SparseMatrixCSC{T,Int64})
  * Matching*Setup = bipartite*matching_setup{T}(x::Vector{T},ei::Vector{Int64},ej::Vector{Int64},m::Int64,n::Int64)
  * Matching*Output = bipartite*matching*primal*dual{T}(rp::Vector{Int64}, ci::Vector{Int64},ai::Vector{T}, m::Int64, n::Int64)
  * Matching*Output = bipartite*matching{T}(A::SparseMatrixCSC{T,Int64})
  * Matching*Output = bipartite*matching{T}(w::Vector{T},ei::Vector{Int64},ej::Vector{Int64},m::Int64,n::Int64)
  * Matching*Output = bipartite*matching{T}(w::Vector{T},ei::Vector{Int64},ej::Vector{Int64})
  * ind = bipartite*matching*indicator{T}(w::Vector{T},ei::Vector{Int64},ej::Vector{Int64})
  * (m1,m2) = edge*list(M*output::Matching_output)
  * S = create*sparse(M*output::Matching_output)

You can check the documentation of each of the output modifiers functions separately.

## Example

```
W = sprand(10,8,0.5)
bipartite_matching(W)
ei = [1;2;3]
ej = [3;2;4]
Matching_Output = bipartite_matching([10;12;13],ei,ej)
Matching_Output.weight
Matching_Output.cardinality
Matching_Output.match
S = create_sparse(bipartite_matching(W)) # get the sparse matrix
(m1,m2) = edge_list(bipartite_matching(W)) # get the edgelist
```
