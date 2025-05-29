```
embed(S::ZZLat, G::Genus, primitive::Bool=true) -> Bool, embedding
```

Return a (primitive) embedding of the integral lattice `S` into some lattice in the genus of `G`.

```jldoctest
julia> G = integer_genera((8,0), 1, even=true)[1];

julia> L, S, i = embed(root_lattice(:A,5), G);

```
