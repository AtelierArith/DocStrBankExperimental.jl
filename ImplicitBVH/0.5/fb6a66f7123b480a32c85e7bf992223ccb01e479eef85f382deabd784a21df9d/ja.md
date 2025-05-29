```
traverse(
    bvh::BVH,
    start_level::Int=default_start_level(bvh),
    cache::Union{Nothing, BVHTraversal}=nothing;
    options=BVHOptions(),
)::BVHTraversal
```

`bvh`を`start_level`から下にトラバースし、すべての接触するバウンディングボリュームリーフを返します。返される[`BVHTraversal`](@ref)には、将来のトラバースで再利用できる2つの接触バッファも含まれています。

# 例

```jldoctest
using ImplicitBVH
using ImplicitBVH: BBox, BSphere

# 簡単なバウンディングスフィアを生成
bounding_spheres = [
    BSphere{Float32}([0., 0., 0.], 0.5),
    BSphere{Float32}([0., 0., 1.], 0.6),
    BSphere{Float32}([0., 0., 2.], 0.5),
    BSphere{Float32}([0., 0., 3.], 0.4),
    BSphere{Float32}([0., 0., 4.], 0.6),
]

# BVHを構築
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32)

# 接触検出のためにBVHをトラバース
traversal = traverse(bvh, 2)

# 将来の接触検出のためにトラバースバッファを再利用 - 異なるBVHでも可能
traversal = traverse(bvh, 2, traversal)
@show traversal.contacts;
;

# 出力
traversal.contacts = Tuple{Int32, Int32}[(1, 2), (2, 3), (4, 5)]
```
