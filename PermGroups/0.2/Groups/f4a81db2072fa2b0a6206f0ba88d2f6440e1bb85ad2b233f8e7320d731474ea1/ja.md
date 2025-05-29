`minimal_words(G::Group)`

は、`G`の各要素に対して、それを表す生成元の最小の正の単語を与える`Dict`を返します。

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
