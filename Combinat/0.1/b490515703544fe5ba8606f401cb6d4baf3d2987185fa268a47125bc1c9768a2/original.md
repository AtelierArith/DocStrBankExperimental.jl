`lcm_partitions(p1,…,pn)`

each  argument is  a partition  of the  same set  `S`, given  as a  list of disjoint  vectors whose  union is  `S`. Equivalently  each argument  can be interpreted as an equivalence relation on `S`.

The result is the finest partition of `S` such that each argument partition refines it. It represents the 'or' of the equivalence relations represented by the arguments.

```julia-repl
julia> lcm_partitions([[1,2],[3,4],[5,6]],[[1],[2,5],[3],[4],[6]])
2-element Vector{Vector{Int64}}:
 [1, 2, 5, 6]
 [3, 4]      
```
