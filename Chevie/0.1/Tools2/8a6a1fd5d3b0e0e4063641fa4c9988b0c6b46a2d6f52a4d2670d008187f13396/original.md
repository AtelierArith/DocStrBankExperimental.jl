`blocks(G::Group,p::Integer)`

Let  `p` be a prime. This function returns the partition of the irreducible characters  of `G`  in `p`-blocks,  represented by  the list  of indices of irreducibles characters in each block.

```julia-repl
julia> W=coxsym(5)
𝔖 ₅

julia> blocks(W,2)
2-element Vector{Vector{Int64}}:
 [1, 3, 4, 5, 7]
 [2, 6]

julia> blocks(W,3)
3-element Vector{Vector{Int64}}:
 [1, 5, 6]
 [2, 3, 7]
 [4]

julia> blocks(W,7)
7-element Vector{Vector{Int64}}:
 [1]
 [2]
 [3]
 [4]
 [5]
 [6]
 [7]
```
