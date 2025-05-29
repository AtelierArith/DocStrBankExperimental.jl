```
type VertexSet
```

Type consisting of a list of `Vertex` objects. It describes the partition of the linear subspace. Object of this type should be constructed using `make_vertex_set` or by `nm_lind` functions. In order to get a list of the vertices from an object of type `vertexset`, one should use `vlist` function, or, for a specific `Vertex`, an getindex function `vertexset[i]`.
