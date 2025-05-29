```
embed_in_unimodular(S::ZZLat, pos::Int, neg::Int, primitive=true, even=true) -> Bool, L, S', iS, iR
```

Return a (primitive) embedding of the integral lattice `S` into some (even) unimodular lattice of signature `(pos, neg)`.

For now this works only for even lattices.

```jldoctest
julia> NS = direct_sum(integer_lattice(:U), rescale(root_lattice(:A, 16), -1))[1];

julia> LK3, iNS, i = embed_in_unimodular(NS, 3, 19);

julia> genus(LK3)
Genus symbol for integer lattices
Signatures: (3, 0, 19)
Local symbol:
  Local genus symbol at 2: 1^22

julia> iNS
Integer lattice of rank 18 and degree 22
with gram matrix
[0   1    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0]
[1   0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    0]
[0   0   -2    1    0    0    0    0    0    0    0    0    0    0    0    0    0    0]
[0   0    1   -2    1    0    0    0    0    0    0    0    0    0    0    0    0    0]
[0   0    0    1   -2    1    0    0    0    0    0    0    0    0    0    0    0    0]
[0   0    0    0    1   -2    1    0    0    0    0    0    0    0    0    0    0    0]
[0   0    0    0    0    1   -2    1    0    0    0    0    0    0    0    0    0    0]
[0   0    0    0    0    0    1   -2    1    0    0    0    0    0    0    0    0    0]
[0   0    0    0    0    0    0    1   -2    1    0    0    0    0    0    0    0    0]
[0   0    0    0    0    0    0    0    1   -2    1    0    0    0    0    0    0    0]
[0   0    0    0    0    0    0    0    0    1   -2    1    0    0    0    0    0    0]
[0   0    0    0    0    0    0    0    0    0    1   -2    1    0    0    0    0    0]
[0   0    0    0    0    0    0    0    0    0    0    1   -2    1    0    0    0    0]
[0   0    0    0    0    0    0    0    0    0    0    0    1   -2    1    0    0    0]
[0   0    0    0    0    0    0    0    0    0    0    0    0    1   -2    1    0    0]
[0   0    0    0    0    0    0    0    0    0    0    0    0    0    1   -2    1    0]
[0   0    0    0    0    0    0    0    0    0    0    0    0    0    0    1   -2    1]
[0   0    0    0    0    0    0    0    0    0    0    0    0    0    0    0    1   -2]

julia> is_primitive(LK3, iNS)
true
```
