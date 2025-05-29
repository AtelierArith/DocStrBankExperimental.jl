```
remove_joint!(g::BVHGraph, v::Integer, v₊₁::Integer = outneighbors(g, v) != [] ? outneighbors(g, v)[1] : 0)
```

頂点 `v` を削除し、周囲の頂点のオフセットと回転を調整して、元の位置からの偏差を最小限に抑えます。

`v` が複数の隣接頂点を持つ場合、回転を調整する際に優先される隣接頂点 `v₊₁` を指定できます。`v` と `v₊₁` は名前で識別することもできます。

参照: [`remove_joints!`](@ref), [`optimize_offsets!`](@ref)
