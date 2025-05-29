`transitive_closure(M)` `transitive_closure!(M)`

`M`   should  be   a  square   boolean  matrix   representing  a  relation; `transitive_closure`  returns a boolean  matrix representing the transitive closure  of  this  relation;  `transitive_closure!`  modifies `M` in place, doing   no  allocations.  The   transitive  closure  is   computed  by  the Floyd-Warshall algorithm, which is quite fast even for large matrices.

```julia-repl
julia> m=[j-i in [0,1] for i in 1:5, j in 1:5]
5×5 Matrix{Bool}:
 1  1  0  0  0
 0  1  1  0  0
 0  0  1  1  0
 0  0  0  1  1
 0  0  0  0  1

julia> transitive_closure(m)
5×5 Matrix{Bool}:
 1  1  1  1  1
 0  1  1  1  1
 0  0  1  1  1
 0  0  0  1  1
 0  0  0  0  1
```
