```
DelaunayMesh()
```

Creates a delaunay triangulation of the points and linearly interpolates between the vertices of the triangle. Really fast interpolation that happens on the GPU (for GLMakie), so optimal for exploring larger timeseries.

!!! warning
    `DelaunayMesh` won't allow you to add a contour plot to the topoplot.


!!! danger
    `DelaunayMesh` will not behave accurately if rendered via CairoMakie, because Cairo (and SVG in general) does not support color maps on meshes.  The color within each triangle will be based only on the values  at the vertices, which causes inaccurate visuals.

