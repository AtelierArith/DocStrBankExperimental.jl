```
poly(vertices, indices; kwargs...)
poly(points; kwargs...)
poly(shape; kwargs...)
poly(mesh; kwargs...)
```

Plots a polygon based on the arguments given. When vertices and indices are given, it functions similarly to `mesh`. When points are given, it draws one polygon that connects all the points in order. When a shape is given (essentially anything decomposable by `GeometryBasics`), it will plot `decompose(shape)`.

```
poly(coordinates, connectivity; kwargs...)
```

Plots polygons, which are defined by `coordinates` (the coordinates of the vertices) and `connectivity` (the edges between the vertices).

## Attributes

Available attributes and their defaults for `AbstractPlotting.Combined{AbstractPlotting.poly!}` are: 

```

```
