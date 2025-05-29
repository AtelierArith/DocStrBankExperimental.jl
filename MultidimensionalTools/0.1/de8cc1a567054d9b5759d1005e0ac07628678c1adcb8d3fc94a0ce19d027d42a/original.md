Given indices, returns an NTuple.  Each element in the NTuple represents a (min, max) tuple for each dimension

```julia
julia> T = [(3, 1), (4, 5), (6, 2), (1, 1)]
4-element Array{Tuple{Int64,Int64},1}:
 (3, 1)
 (4, 5)
 (6, 2)
 (1, 1)
 
julia> findmax_indices(T)
1×2 Array{Tuple{Int64,Int64},2}:
(1, 6)  (1, 5)
```
