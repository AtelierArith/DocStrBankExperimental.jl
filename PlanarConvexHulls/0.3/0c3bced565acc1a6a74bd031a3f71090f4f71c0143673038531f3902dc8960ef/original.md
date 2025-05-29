```julia
is_ordered_and_strongly_convex(vertices, order)

```

Return whether `vertices` are ordered according to vertex order type `O` (a subtype of [`VertexOrder`](@ref)), and as a result *strongly* convex (see e.g. [CGAL documentation](https://doc.cgal.org/latest/Convex_hull_2/index.html) for a definition of strong convexity).
