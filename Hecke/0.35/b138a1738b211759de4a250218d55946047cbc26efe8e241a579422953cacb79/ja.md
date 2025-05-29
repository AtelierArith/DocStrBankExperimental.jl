```
embed(S::ZZLat, G::Genus, primitive::Bool=true) -> Bool, embedding
```

整数格 `S` を `G` の属する格のいずれかに（原始的に）埋め込みます。

```jldoctest
julia> G = integer_genera((8,0), 1, even=true)[1];

julia> L, S, i = embed(root_lattice(:A,5), G);

```
