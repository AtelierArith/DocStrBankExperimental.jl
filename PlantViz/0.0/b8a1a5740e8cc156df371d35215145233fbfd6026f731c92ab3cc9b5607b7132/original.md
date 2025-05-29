```
render!(source::Source{G, A, nw}; n = 20, alpha = 0.2, point = false,
        scale = 0.2)
```

Add a mesh representing the light source to a 3D scene (if `point = false`) or a series of points representing the center of the light sources (if `point = true`). When `point = false`, for each type of light source a triangular mesh will be created, where `n` is the number of triangles (see documentation of geometric primitives for details) and `alpha` is the transparency to be used for each triangle. When `point = true`, only the center of the light source is rendered along with the normal vector at that point (representative of the direction at which rays are generated). In the current version, `point = true` is only possible for directional light sources.
