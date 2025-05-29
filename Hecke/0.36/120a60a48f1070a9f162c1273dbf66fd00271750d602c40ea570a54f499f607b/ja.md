```
embed_in_unimodular(S::ZZLat, pos::Int, neg::Int, primitive=true, even=true) -> Bool, L, S', iS, iR
```

整数格 `S` を、署名 `(pos, neg)` のいくつかの（偶数の）ユニモジュラー格に（原始的に）埋め込みます。

現時点では、これは偶数格に対してのみ機能します。

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
