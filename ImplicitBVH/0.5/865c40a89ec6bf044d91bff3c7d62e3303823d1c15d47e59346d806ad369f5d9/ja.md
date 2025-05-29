```
traverse_rays(
    bvh::BVH,
    points::AbstractArray,
    directions::AbstractArray,
    start_level::Int=1,
    cache::Union{Nothing, BVHTraversal}=nothing;
    options=BVHOptions(),
)::BVHTraversal
```

`points`（形状 `(3, N)`）と `directions`（形状 `(3, N)`）で定義された N 本のレイの集合と、`bvh` 内のいくつかのバウンディングボリュームとの交差を計算します。

前方レイのみがカウントされます - すなわち、方向が重要です。

返される [`BVHTraversal`](@ref) の `.contacts` フィールドには、`bvh.leaves` と `axes(points, 2)` の順序に従ったインデックスペア `(iboundingvolume, iray)` が含まれます。

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

# ポイントソースと方向で定義された2本のレイを生成
points = [
    0.  0 
    0.  0
    -1 -1
]

# 1本のレイはすべてのバウンディングボリュームを通過し、もう1本は下に向かっており通過しない
directions = [
    0.  0
    0.  0
    1.  -1
]

# BVHを構築
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32)

# 接触検出のためにBVHをトラバース
traversal = traverse_rays(bvh, points, directions)

# 将来の接触検出のためにトラバースバッファを再利用 - おそらく異なるBVHで
traversal = traverse_rays(bvh, points, directions, 2, traversal)
@show traversal.contacts;
;

# 出力
traversal.contacts = Tuple{Int32, Int32}[(1, 1), (2, 1), (3, 1), (4, 1), (5, 1)]
```
