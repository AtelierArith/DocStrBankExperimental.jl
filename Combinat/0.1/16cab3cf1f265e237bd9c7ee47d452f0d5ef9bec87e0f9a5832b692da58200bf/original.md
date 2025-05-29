`partitions(n::Integer,set::AbstractVector[,k])`, `npartitions(n::Integer,set::AbstractVector[,k])`   

returns  the list  of partitions  of `n`  (with `k`  parts if `k` is given) restricted  to have parts in `set`. `npartitions` gives (faster) the number of such partitions.

Let  us show how many ways there are to pay 17 cents using coins of 2,5 and 10 cents.

```julia-repl
julia> npartitions(17,[10,5,2])
3

julia> partitions(17,[10,5,2])
3-element Vector{Vector{Int64}}:
 [5, 2, 2, 2, 2, 2, 2]
 [5, 5, 5, 2]
 [10, 5, 2]

julia> npartitions(17,[10,5,2],3) # pay with 3 coins
1

julia> partitions(17,[10,5,2],3) 
1-element Vector{Vector{Int64}}:
 [10, 5, 2]
```
