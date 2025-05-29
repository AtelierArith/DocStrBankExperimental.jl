```julia
plot_triangulateio(
    Plotter,
    tio::Triangulate.TriangulateIO;
    axis,
    voronoi,
    aspect,
    circumcircles
) -> Any

```

Plot contents of triangulateio structure. The plot module is passed as parameter. This allows to keep the package free of heavy plot package dependencies. 
