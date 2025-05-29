`minimal_words(G::Group)`

returns  a `Dict` giving for each element of `G` a minimal positive word in the generators representing it.

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3));
julia> minimal_words(G)
OrderedDict{Perm{Int16}, Vector{Int64}} with 6 entries:
  ()      => []
  (1,2)   => [1]
  (1,2,3) => [2]
  (1,3)   => [1, 2]
  (2,3)   => [2, 1]
  (1,3,2) => [2, 2]
```
