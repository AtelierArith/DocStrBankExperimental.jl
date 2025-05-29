`sstab_onmats([G,]M[,l])`

if  the argument `G`  is given (which  should be an  `SPermGroup`) this is just  a fast implementation of `centralizer(G,M,onmats)`. If `G` is omitted it  is  taken  to  be  `hyperoctaedral_group(size(M,1))`.  The program uses sophisticated  algorithms, and can  handle matrices up  to 80×80. If `l` is given the return group should also centralize `l` (for the action ^)

```julia-repl
julia> n=[-1 -1 -1 -2 2 -2 -3 -3 -3; -1 -1 -1 -3 3 -3 -2 -2 -2; -1 -1 -1 -1 1 -1 -1 -1 -1; -2 -3 -1 -3 1 -2 -1 -3 -2; 2 3 1 1 -2 3 3 2 1; -2 -3 -1 -2 3 -1 -2 -1 -3; -3 -2 -1 -1 3 -2 -2 -3 -1; -3 -2 -1 -3 2 -1 -3 -1 -2; -3 -2 -1 -2 1 -3 -1 -2 -3];

julia> length(sstab_onmats(n))
8
```
