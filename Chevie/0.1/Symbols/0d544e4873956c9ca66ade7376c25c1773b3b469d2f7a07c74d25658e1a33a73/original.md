`symbol_partition_tuple(p, s)` symbol of shape `s` for partition tuple `p`.

In  the general case, `s` is a `Vector{Int}`  of same length as `p` and the `i`-th  element of the result is the β-set for `pᵢ` shifted to be of length `sᵢ` (the minimal integer which makes this possible is added to `s`).

When  `s` is  a positive  integer it  is interpreted  as `[s,0,0,…]`  and a negative  integer is interpreted  as `[0,-s,-s,…]` so  when `p` is a double partition  one gets the  symbol of defect  `s` associated to  `p`; as other uses  the  unipotent  symbol  for  a  character  of the principal series of `G(e,1,r)`   parameterized   by   an   `e`-tuple   `p`   of  partitions  is `symbol_partition_tuple(p,1)` and for `G(e,e,r)` the similar computation is `symbol_partition_tuple(p,0)`  (the function handles coded periodic `p` for `G(e,e,r)`).

```julia-repl
julia> symbol_partition_tuple([[2,1],[1]],1)
2-element Vector{Vector{Int64}}:
 [1, 3]
 [1]

julia> symbol_partition_tuple([[2,1],[1]],0)
2-element Vector{Vector{Int64}}:
 [1, 3]
 [0, 2]

julia> symbol_partition_tuple([[2,1],[1]],-1)
2-element Vector{Vector{Int64}}:
 [1, 3]
 [0, 1, 3]
```
