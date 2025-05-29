```
function get_node_boundary_tags(triout::TriangulateIO,md::MeshData{2},rd::RefElemData{2,Tri})
```

`node_tags` = `Nfp` x `Nfaces * num_elements` 配列を計算します。ここで、各エントリは Triangulate.jl タグ番号です。
