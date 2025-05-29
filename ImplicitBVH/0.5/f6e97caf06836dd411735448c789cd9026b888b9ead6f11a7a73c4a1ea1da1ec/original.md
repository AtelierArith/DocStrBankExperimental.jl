```julia
struct BVH{I<:Integer, VN<:(AbstractVector), VL<:(AbstractVector), VM<:(AbstractVector), VO<:(AbstractVector)}
```

Implicit bounding volume hierarchy constructed from an iterable of some geometric primitives' (e.g. triangles in a mesh) bounding volumes forming the [`ImplicitTree`](@ref) leaves. The leaves and merged nodes above them can have different types - e.g. `BSphere{Float64}` for leaves merged into larger `BBox{Float64}`.

The initial geometric primitives are sorted according to their Morton-encoded coordinates; the unsigned integer type used for the Morton encoding can be chosen between `Union{UInt16, UInt32, UInt64}`.

Finally, the tree can be incompletely-built up to a given `built_level` and later start contact detection downwards from this level, e.g.:

```
Implicit tree from 5 bounding volumes - i.e. the real leaves

Tree Level          Nodes & Leaves               Build Up    Traverse Down
    1                     1                         Ʌ              |
    2             2               3                 |              |
    3         4       5       6        7v           |              |
    4       8   9   10 11   12 13v  14v  15v        |              V
            -------Real------- ---Virtual---
```

Note: in order to not mutate the leaves (you may store them somewhere else, and this avoids making a copy), we save the sorted order of the BVH leaves inside the `order` field.

# Methods

```
# Normal constructor which builds BVH
BVH(
    bounding_volumes::AbstractVector{L},
    node_type::Type{N}=L,
    morton_type::Type{U}=UInt32,
    built_level=1,
    cache::Union{Nothing, BVH}=nothing;
    options=BVHOptions(),
) where {L, N, U <: MortonUnsigned}
```

# Fields

  * `tree::`[`ImplicitTree`](@ref)`{I <: Integer}`
  * `nodes::VN <: AbstractVector`
  * `leaves::VL <: AbstractVector`
  * `mortons::VM <: AbstractVector`
  * `order::VO <: AbstractVector`
  * `built_level::Int`

# Examples

Simple usage with bounding spheres and default 64-bit types:

```jldoctest
using ImplicitBVH
using ImplicitBVH: BSphere

# Generate some simple bounding spheres
bounding_spheres = [
    BSphere([0., 0., 0.], 0.5),
    BSphere([0., 0., 1.], 0.6),
    BSphere([0., 0., 2.], 0.5),
    BSphere([0., 0., 3.], 0.4),
    BSphere([0., 0., 4.], 0.6),
]

# Build BVH
bvh = BVH(bounding_spheres)

# Traverse BVH for contact detection
traversal = traverse(bvh)
@show traversal.contacts;
;

# output
traversal.contacts = Tuple{Int32, Int32}[(1, 2), (2, 3), (4, 5)]
```

Using `Float32` bounding spheres for leaves, `Float32` bounding boxes for nodes above, and `UInt32` Morton codes:

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
traversal = traverse(bvh)
@show traversal.contacts;
;

# output
traversal.contacts = Tuple{Int32, Int32}[(1, 2), (2, 3), (4, 5)]
```

Build BVH up to level 2 and start traversing down from level 3, reusing the previous traversal cache:

```julia
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32, 2)
traversal = traverse(bvh, 3, traversal)
```

Reuse previous BVH memory for a new BVH (specifically, the nodes, mortons, and order vectors, but not the leaves):

```julia
bvh = BVH(bounding_spheres, BBox{Float32}, UInt32, 1, bvh)
```
