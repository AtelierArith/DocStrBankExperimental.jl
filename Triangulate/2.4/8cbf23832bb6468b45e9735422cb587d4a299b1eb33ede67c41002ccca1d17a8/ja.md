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

triangulateio構造体の内容をプロットします。プロットモジュールはパラメータとして渡されます。これにより、パッケージは重いプロットパッケージの依存関係から解放されます。
