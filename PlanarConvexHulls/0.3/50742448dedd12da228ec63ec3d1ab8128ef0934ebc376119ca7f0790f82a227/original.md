```julia
struct ConvexHull{O<:PlanarConvexHulls.VertexOrder, T, P<:StaticArrays.StaticArray{Tuple{2}, T, 1}, V<:AbstractArray{P<:StaticArrays.StaticArray{Tuple{2}, T, 1}, 1}}
```

Represents the convex hull of a set of 2D points by its extreme points (vertices), which are stored according to the [`VertexOrder`](@ref) given by the first type parameter.
