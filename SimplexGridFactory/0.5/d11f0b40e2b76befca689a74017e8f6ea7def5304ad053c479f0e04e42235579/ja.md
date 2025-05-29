```julia
simplexgrid(
    ::Type{SimplexGridFactory.TriangulateType},
    Triangulate,
    input;
    kwargs...
) -> ExtendableGrids.ExtendableGrid

```

三角形の入力データからグリッドを作成します。

利用可能な `kwargs` については [`default_options`](@ref) を参照してください。
