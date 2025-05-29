'reorder(U,l[,order])'

This  function  takes  a  list  of  pairs  'r=>c'  representing a unipotent element,  where 'r'  is a  root and  'c' the corresponding coefficient, and puts  it in  canonical form,  reordering the  terms to agree with 'U.order' using  the commutation  relations. If  a second  argument is given, this is used instead of 'U.order'.

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2))
UnipotentGroup(G₂)

julia> l=reorder(U,[2=>4,1=>2])
6-element Vector{Pair{Int64, Int64}}:
 1 => 2
 2 => 4
 3 => -8
 4 => 32
 5 => -128
 6 => 512

julia> reorder(U,l,6:-1:1)
2-element Vector{Pair{Int64, Int64}}:
 2 => 4
 1 => 2
```
