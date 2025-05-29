`gcd_partitions(p1,…,pn)`

Each  argument is  a partition  of the  same set  `S`, given  as a  list of disjoint  vectors whose  union is  `S`. Equivalently  each argument  can be interpreted as an equivalence relation on `S`.

The result is the coarsest partition which refines all argument partitions. It  represents the  'and' of  the equivalence  relations represented by the arguments.

```julia-repl
julia> gcd_partitions([[1,2],[3,4],[5,6]],[[1],[2,5],[3],[4],[6]])
6-element Vector{Vector{Int64}}:
 [1]
 [2]
 [3]
 [4]
 [5]
 [6]
```
