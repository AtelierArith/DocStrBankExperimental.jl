```
hyperbolic_plane_lattice(n::RationalUnion = 1) -> ZZLat
```

Return the hyperbolic plane with intersection form of scale `n`, that is, the unique (up to isometry) even unimodular hyperbolic $\mathbb Z$-lattice of rank 2, rescaled by `n`.

# Examples

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
