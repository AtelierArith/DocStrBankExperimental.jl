```
grouped_nearest(tree::KDTree, siteindex::Int, nsites::Int; atol=1e-8)
```

`siteindex`に最も近い`nsites`個の頂点を見つけ、それらを距離でグループ化します。距離の差が`atol`（デフォルトは`1e-8`）より小さい場合は同じものとして扱われます。[`DistanceGroup`](@ref)インスタンスを返します。

```jldoctest; setup=:(using BloqadeLattices)
julia> atoms = generate_sites(HoneycombLattice(), 5, 5);

julia> tree = make_kdtree(atoms);

julia> gn = grouped_nearest(tree, 23, 20)
DistanceGroup([23, 14, 22, 24, 15, 13, 21, 25, 33, 31, 12, 16, 32, 4, 6, 34, 26, 17, 5, 41], [1, 2, 5, 11, 14, 18, 21])

julia> gn[0]  # 0番目の最近接隣接点は頂点自体によって定義されます
1-element Vector{Int64}:
 23

julia> gn[1]  # 最近接隣接点
3-element Vector{Int64}:
 14
 22
 24

julia> gn[2]  # 2番目の最近接隣接点
6-element Vector{Int64}:
 15
 13
 21
 25
 33
 31
```
