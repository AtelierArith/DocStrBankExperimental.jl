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

Compute the intersections between a set of N rays defined by `points` (shape `(3, N)`) and `directions` (shape, `(3, N)`), and some bounding volumes inside a `bvh`.

Only forward rays are counted - i.e. the direction matters.

The returned [`BVHTraversal`](@ref) `.contacts` field will contain the index pairs `(iboundingvolume, iray)` following the order in `bvh.leaves` and `axes(points, 2)`.

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

# Generate two rays, each defined by a point source and direction
points = [
    0.  0 
    0.  0
    -1 -1
]

# One ray passes through all bounding volumes, the other goes downwards and does not
directions = [
    0.  0
    0.  0
    1.  -1
]

# Build BVH
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32)

# Traverse BVH for contact detection
traversal = traverse_rays(bvh, points, directions)

# Reuse traversal buffers for future contact detection - possibly with different BVHs
traversal = traverse_rays(bvh, points, directions, 2, traversal)
@show traversal.contacts;
;

# output
traversal.contacts = Tuple{Int32, Int32}[(1, 1), (2, 1), (3, 1), (4, 1), (5, 1)]
```
