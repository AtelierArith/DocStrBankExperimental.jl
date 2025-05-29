```
plot_cell_data(mesh::JutulMesh, data::Vector; kwarg...)
plot_cell_data(mesh, data;
    cells = nothing,
    faces = nothing,
    boundaryfaces = nothing
)
```

メッシュ上にセル単位の値（ベクトルとして）をプロットします。オプションとして、特定のエンティティの選択に制限するために、インデックス `cells`、`faces` または `boundaryfaces` を渡すことができます。
