```
hyperbolic_plane_lattice(n::RationalUnion = 1) -> ZZLat
```

スケール `n` の交差形式を持つ双曲平面を返します。すなわち、`n` でスケールされたランク 2 の一意な（同型に関して）偶数単位的双曲 $\mathbb Z$-格子です。

# 例

```jldoctest
julia> L = hyperbolic_plane_lattice(6);

julia> gram_matrix(L)
[0   6]
[6   0]

julia> L = hyperbolic_plane_lattice(ZZ(-13));

julia> gram_matrix(L)
[  0   -13]
[-13     0]
```
