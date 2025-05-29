`minimal_words(G::Group,w)`

Gは、最小の長さの生成子の言葉としての`w`のすべての表現を返します（`minimal_words(G)`を使用）。

```julia-repl
julia> G=Group(Perm(1,2),Perm(2,3));

julia> minimal_words(G,Perm(1,3))
2-element Vector{Vector{Int64}}:
 [1, 2, 1]
 [2, 1, 2]
```
