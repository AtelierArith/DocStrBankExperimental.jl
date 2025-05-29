`orbit(gens::AbstractVector,p,action::Function=^)`

`orbit(G::Group,p,action::Function=^)`

the orbit of point `p` under repeated action of generators `gens`. The type of  point `p` should be hashable. The  default action of a group element is `^`.  For example if `g` is a permutation  and `p` an integer, `p^g` is the image  of `p` by `g`; if `h` and  `g` are group elements, then `h^g` is the conjugate  `inv(g)*h*g`. If  a group  is given  instead of  generators, the orbit under `gens(G)` is returned.

```julia-repl
julia> orbit([Perm(1,2),Perm(2,3)],1)
3-element Vector{Int64}:
 1
 2
 3

julia> orbit([Perm(1,2),Perm(2,3)],[1,3],ontuples)
6-element Vector{Vector{Int64}}:
 [1, 3]
 [2, 3]
 [1, 2]
 [3, 2]
 [2, 1]
 [3, 1]

julia> orbit([Perm(1,2),Perm(2,3)],[1,3],(v,g)->sort(v.^g)) # "OnSets"
3-element Vector{Vector{Int64}}:
 [1, 3]
 [2, 3]
 [1, 2]
```
