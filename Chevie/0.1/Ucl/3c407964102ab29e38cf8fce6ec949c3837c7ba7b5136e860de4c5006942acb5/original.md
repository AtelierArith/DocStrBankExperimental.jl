'special_pieces(<uc>)'

The special pieces form a partition of the unipotent variety of a reductive group   `𝐆`   which   was   first   defined   in   [Spaltenstein1982  chap. III](biblio.htm#spalt82)  as the fibres  of `d^2`, where  `d` is a "duality map". Another definition is as the set of classes in the Zariski closure of a  special class  and not  in the  Zariski closure  of any  smaller special class,  where a  special class  is the  support of  the image  of a special character by the Springer correspondence.

Each  piece is a union of unipotent  conjugacy classes so is represented in Chevie  as a  list of  class numbers.  Thus the  list of  special pieces is returned  as  a  list  of  lists  of  class  numbers. The list is sorted by increasing  piece dimension, while each piece is sorted by decreasing class dimension, so that the special class is listed first.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> special_pieces(UnipotentClasses(W))
3-element Vector{Vector{Int64}}:
 [1]
 [4, 3, 2]
 [5]

julia> special_pieces(UnipotentClasses(W,3))
3-element Vector{Vector{Int64}}:
 [1]
 [4, 3, 2, 6]
 [5]
```

The   example  above  shows  that  the  special  pieces  are  different  in characteristic 3.
