`words(G::Group)`

は、`G` の各要素に対してそれを表す生成子の正の単語を返す `Dict` を返します。これは `minimal_words` よりも速いですが、単語が最小であることは保証されていません。

```julia-repl
julia> G=Group(Perm(1,2),Perm(1,2,3));
julia> words(G)
OrderedDict{Perm{Int16}, Vector{Int64}} with 6 entries:
  ()      => []
  (1,2)   => [1]
  (1,2,3) => [2]
  (1,3)   => [1, 2]
  (2,3)   => [2, 1]
  (1,3,2) => [1, 2, 1]
```
