```
function get_node_boundary_tags(triout::TriangulateIO,md::MeshData{2},rd::RefElemData{2,Tri})
```

Computes `node_tags` = `Nfp` x `Nfaces * num_elements` array where each entry is a Triangulate.jl tag number.
