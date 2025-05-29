`orbits(gens::Vector,v,action=^;trivial=true)`

`orbits(G,v,action=^;trivial=true)`

the  orbits on `v`  of the repeated  action of `gens`;  the elements of `v` should  be hashable. If a  group is given instead  of generators, the orbit under  `gens(G)` is returned. If `trivial=false` the one-element orbits are not returned.

```julia-repl
julia> G=Group(Perm(1,2),Perm(2,3));
julia> orbits(G,1:4)
2-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [4]
```
