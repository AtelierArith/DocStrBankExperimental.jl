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

Return all the `bvh1` bounding volume leaves that are in contact with any in `bvh2`. The returned [`BVHTraversal`](@ref) also contains two contact buffers that can be reused on future traversals.

# Examples

```jldoctest
using ImplicitBVH
using ImplicitBVH: BBox, BSphere

# Generate some simple bounding spheres
bounding_spheres1 = [
    BSphere{Float32}([0., 0., 0.], 0.5),
    BSphere{Float32}([0., 0., 3.], 0.4),
]

bounding_spheres2 = [
    BSphere{Float32}([0., 0., 1.], 0.6),
    BSphere{Float32}([0., 0., 2.], 0.5),
    BSphere{Float32}([0., 0., 4.], 0.6),
]

# Build BVHs
bvh1 = BVH(bounding_spheres1, BBox{Float32}, UInt32)
bvh2 = BVH(bounding_spheres2, BBox{Float32}, UInt32)

# Traverse BVH for contact detection
traversal = traverse(bvh1, bvh2, default_start_level(bvh1), default_start_level(bvh2))

# Reuse traversal buffers for future contact detection - possibly with different BVHs
traversal = traverse(bvh1, bvh2, default_start_level(bvh1), default_start_level(bvh2), traversal)
@show traversal.contacts;
;

# output
traversal.contacts = Tuple{Int32, Int32}[(1, 1), (2, 3)]
```
