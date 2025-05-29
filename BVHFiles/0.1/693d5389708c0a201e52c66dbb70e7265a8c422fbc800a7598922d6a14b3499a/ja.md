```
remove_joints!(g::BVHGraph, names::AbstractString...)
```

`names` にあるすべての頂点を削除し、周囲の頂点のオフセットと回転を調整して、元の位置からの偏差を最小限に抑えます。

関連情報: [`remove_joint!`](@ref), [`optimize_offsets!`](@ref)
