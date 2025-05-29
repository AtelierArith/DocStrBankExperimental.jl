```
traverse(
    bvh1::BVH,
    bvh2::BVH,
    start_level1::Int=default_start_level(bvh1),
    start_level2::Int=default_start_level(bvh2),
    cache::Union{Nothing, BVHTraversal}=nothing;
    options=BVHOptions(),
)::BVHTraversal
```

`bvh1`のバウンディングボリュームリーフのうち、`bvh2`のいずれかと接触しているものを返します。返される[`BVHTraversal`](@ref)には、将来のトラバーサルで再利用できる2つの接触バッファも含まれています。

# 例

```jldoctest
using ImplicitBVH
using ImplicitBVH: BBox, BSphere

# 簡単なバウンディングスフィアを生成
bounding_spheres1 = [
    BSphere{Float32}([0., 0., 0.], 0.5),
    BSphere{Float32}([0., 0., 3.], 0.4),
]

bounding_spheres2 = [
    BSphere{Float32}([0., 0., 1.], 0.6),
    BSphere{Float32}([0., 0., 2.], 0.5),
    BSphere{Float32}([0., 0., 4.], 0.6),
]

# BVHを構築
bvh1 = BVH(bounding_spheres1, BBox{Float32}, UInt32)
bvh2 = BVH(bounding_spheres2, BBox{Float32}, UInt32)

# 接触検出のためにBVHをトラバース
traversal = traverse(bvh1, bvh2, default_start_level(bvh1), default_start_level(bvh2))

# 将来の接触検出のためにトラバーサルバッファを再利用 - 異なるBVHでも可能
traversal = traverse(bvh1, bvh2, default_start_level(bvh1), default_start_level(bvh2), traversal)
@show traversal.contacts;
;

# 出力
traversal.contacts = Tuple{Int32, Int32}[(1, 1), (2, 3)]
```
