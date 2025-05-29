```
plot_mesh(mesh)
plot_mesh(mesh;
    cells = nothing,
    faces = nothing,
    boundaryfaces = nothing,
    outer = false,
    color = :lightblue,
)

メッシュを均一な色でプロットします。オプションとして、特定のエンティティの選択に制限するために、インデックス `cells`、`faces`、または `boundaryfaces` を渡すことができます。
```
