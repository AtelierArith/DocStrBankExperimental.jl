`minimal_words(G::Group,w)`

Gives all expressions of `w` as words in the generators of `G` of minimal length (uses `minimal_words(G)`).

```julia-repl
julia> G=Group(Perm(1,2),Perm(2,3));

julia> minimal_words(G,Perm(1,3))
2-element Vector{Vector{Int64}}:
 [1, 2, 1]
 [2, 1, 2]
```
