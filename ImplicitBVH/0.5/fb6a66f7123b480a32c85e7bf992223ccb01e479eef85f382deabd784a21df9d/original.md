```
traverse(
    bvh::BVH,
    start_level::Int=default_start_level(bvh),
    cache::Union{Nothing, BVHTraversal}=nothing;
    options=BVHOptions(),
)::BVHTraversal
```

Traverse `bvh` downwards from `start_level`, returning all contacting bounding volume leaves. The returned [`BVHTraversal`](@ref) also contains two contact buffers that can be reused on future traversals.

# Examples

```jldoctest
using ImplicitBVH
using ImplicitBVH: BBox, BSphere

# Generate some simple bounding spheres
bounding_spheres = [
    BSphere{Float32}([0., 0., 0.], 0.5),
    BSphere{Float32}([0., 0., 1.], 0.6),
    BSphere{Float32}([0., 0., 2.], 0.5),
    BSphere{Float32}([0., 0., 3.], 0.4),
    BSphere{Float32}([0., 0., 4.], 0.6),
]

# Build BVH
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32)

# Traverse BVH for contact detection
traversal = traverse(bvh, 2)

# Reuse traversal buffers for future contact detection - possibly with different BVHs
traversal = traverse(bvh, 2, traversal)
@show traversal.contacts;
;

# output
traversal.contacts = Tuple{Int32, Int32}[(1, 2), (2, 3), (4, 5)]
```
